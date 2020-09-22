<div align="center">

## A more efficient way of saving small bits of data


</div>

### Description

This article can work with all programming languages (examples in VB for ease of understanding). If you have ever worked with a database with TONS of Yes/No (Access) or Bit (SQL Server) fields, this article can help cut down database size, for example, or memory if you use individual variables to hold True or False values.
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Derreck Dean](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/derreck-dean.md)
**Level**          |Advanced
**User Rating**    |4.4 (22 globes from 5 users)
**Compatibility**  |VB 3\.0, VB 4\.0 \(16\-bit\), VB 4\.0 \(32\-bit\), VB 5\.0, VB 6\.0, VB Script, ASP \(Active Server Pages\) , VBA MS Access, VBA MS Excel
**Category**       |[Coding Standards](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/coding-standards__1-43.md)
**World**          |[Visual Basic](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/visual-basic.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/derreck-dean-a-more-efficient-way-of-saving-small-bits-of-data__1-34651/archive/master.zip)





### Source Code

<font size=2 style="font-size: 8pt;" face="tahoma,verdana,helvetica,arial">
<b>Saving DB Size/Program Memory by using the AND operator and numeric variables</b><BR><BR>
This article can work with all programming languages (examples in VB for ease of understanding). If you have ever worked with a database with TONS of Yes/No (Access) or Bit (SQL Server) fields, this article can help cut down database size, for example, or memory if you use individual variables to hold True or False values.<BR><BR>
This example applies more to database coding more than memory management, but use as you like.<BR><BR>
Suppose you have 5 variables, all holding a Boolean value. The variables are boolIsMale, boolIsFemale, boolHasDog, boolHasCat, boolHasFish.
If you were to make this one single variable, it would be easier to process this data. What we do is declare a variable as a LONG type and set it to zero.<BR><BR>
Declare lngPerson as Long<BR>
lngPerson = 0<BR><BR>
Through commenting your code (so you don't forget, set representations of each of those Boolean values above to a number. This is important - the numbers have to be either a number one (1) or a power of 2 (2, 4, 8, 16, 32, et. al).<BR><BR>
' Is male = 1<BR>
' Is female = 2<BR>
' Has cat = 4<BR>
' Has dog = 8<BR>
' Has fish = 16<BR><BR>
To say that this particular person for example was FEMALE, and has a CAT and a DOG, you would assign the variable to the sum of those numbers.<BR><BR>
lngPerson = 2 + 4 + 8<BR><BR>
Now what about READING the variable? This is simple.<BR><BR>
bool_ret_val = (longval AND test_num) = test_num
<BR><BR>To retrieve a boolean value for the example above, use the statement to test whether this person has a DOG (the representation for dog is 8 as in the comments).<BR><BR>
boolHasDog = (lngPerson AND 8) = 8<BR><BR>
Since this person does not have fish (we did not add 16 to lngPerson above), this next example would return False.
boolHasFish = (lngPerson AND 16) = 16<BR><BR>
The expression (lngPerson AND 16) would actually return 0.<BR><BR>
For a more real-world example, if you have an SQL Server database that holds a table with a LOT of BIT fields (1's and 0's representing True and False for those still stuck using Access), you can cut down easily on the size of the database by making a numeric field and using the above example as a base for your programming. But heed this word of caution - you need a field bigger than INT if you're combining a lot of fields - Watch how quickly powers of 2 grow!<BR><BR>
1,2,4,8,16,32,64,128,256,512,1024,2048,4096,8192,16384,32768,65536,...<BR><BR>
For the VB integer, the above already constitutes as an overflow. Make sure you use a LONG variable.<BR><BR>
Please make sure to post comments if you need more help, and vote if you like!<BR><BR>
- Derreck
</font>

