<div align="center">

## Basic Free Threading


</div>

### Description

Basic Free Threading
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Petko Petkov](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/petko-petkov.md)
**Level**          |Beginner
**User Rating**    |5.0 (20 globes from 4 users)
**Compatibility**  |VB\.NET
**Category**       |[System Services/ Functions](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/system-services-functions__10-23.md)
**World**          |[\.Net \(C\#, VB\.net\)](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/net-c-vb-net.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/petko-petkov-basic-free-threading__10-1515/archive/master.zip)





### Source Code

<p><b>Free Threading</b></p>
<p>For the first time, VB.NET has given VB developers the ability to write truly
 freethreaded<br>
 applications. If your application is going to perform a task that could take
 a<br>
 long time, such as parsing through a large recordset or performing a complex
 series<br>
 of mathematical calculations, you can push that processing off to its own thread
 so<br>
 that the rest of your application is still accessible. In VB6, the best you
 could do to<br>
 keep the rest of the application from appearing to be locked was to use the
 DoEvents<br>
 method.</p>
<p>Examine this code, which is written for VB.NET. Here you have some code for<br>
 button1. This code calls the BeBusy routine, which has a loop in it to just
 to take up<br>
 time. However, while in this loop, you are consuming the thread for this application,<br>
 and the UI will not respond while the loop is running. </p>
<p>Open a new VB project. Add a button.</p>
<p><font color="#3366FF">Private Sub</font> button1_Click(<font color="#3366FF">ByVal</font>
 sender <font color="#3366FF">As</font> System.Object, _<br>
 &nbsp;&nbsp;<font color="#3366FF">ByVal</font> e <font color="#3366FF">As</font>
 System.EventArgs) <font color="#3366FF">Handles</font> button1.Click<br>
 &nbsp;&nbsp;BeBusy()<br>
 End Sub<br>
 <br>
 <font color="#3366FF">Sub</font> BeBusy()<br>
 <font color="#3366FF">Dim</font> i <font color="#3366FF">As Decimal</font><br>
 &nbsp;&nbsp;<font color="#3366FF">For</font> i = 1 <font color="#3366FF">To</font>
 20000000<br>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#009933">&#145;do nothing but
 tie up app</font><br>
 &nbsp;&nbsp;<font color="#3366FF">Next</font><br>
 &nbsp;&nbsp;Beep()<br>
 End Sub </p>
<p>To create a thread, you must use the System.Threading.Thread class.</p>
<p><font color="#3366FF">Imports</font> System.Threading.Thread<br>
</p>
<p>To fix the code and keep BeBusy from consuming the main program thread, you
 have<br>
 now created a new thread and will run BeBusy on that thread. However, that line
 of<br>
 code isn&#146;t enough. Next, you must call the Start method on that new thread.
 With<br>
 VB.NET, calling BeBusy on its own thread would look like this:<br>
 <br>
 <font color="#3366FF">Private Sub</font> button1_Click(<font color="#3366FF">ByVal</font>
 sender <font color="#3366FF">As</font> System.Object, _<br>
 &nbsp;&nbsp;<font color="#3366FF">ByVal</font> e <font color="#3366FF">As</font>
 System.EventArgs) Handles button1.Click<br>
 &nbsp;&nbsp;<br>
 &nbsp;&nbsp; <font color="#FFFFFF">'<font color="#009933">Creatre a new thread</font></font><br>
 &nbsp;&nbsp;<font color="#3366FF">Dim</font> busyThread <font color="#3366FF">As
 New </font>System.Threading.Thread(<font color="#3366FF">AddressOf</font> BeBusy)<br>
 &nbsp;&nbsp;busyThread.Start()<br>
 End Sub </p>

