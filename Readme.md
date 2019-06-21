<!-- default file list -->
*Files to look at*:

* [BootstrapChartDataItem.cs](./CS/App_Code/BootstrapChartDataItem.cs) (VB: [BootstrapChartDataItem.vb](./VB/App_Code/BootstrapChartDataItem.vb))
* [Default.aspx](./CS/Default.aspx) (VB: [Default.aspx](./VB/Default.aspx))
* [Default.aspx.cs](./CS/Default.aspx.cs) (VB: [Default.aspx.vb](./VB/Default.aspx.vb))
<!-- default file list end -->
# BootstrapChart - How to bind to filtered or sorted ASPxGridView data on the client side at runtime
<!-- run online -->
**[[Run Online]](https://codecentral.devexpress.com/t555410/)**
<!-- run online end -->


<p>This example demonstrates how to show filtered or sorted <a href="https://documentation.devexpress.com/AspNet/DevExpress.Web.ASPxGridView.members">ASPxGridView</a> data in <a href="https://documentation.devexpress.com/AspNetBootstrap/DevExpress.Web.Bootstrap.BootstrapChart.members">BootstrapChart</a> on a callback at runtime by using client side data binding.<br><br>In page markup, enable ASPxGridView’s <a href="https://documentation.devexpress.com/AspNet/DevExpress.Web.ASPxGridViewSettings.ShowFilterRow.property">ShowFilterRow</a> property to show <a href="https://documentation.devexpress.com/AspNet/3753/ASP-NET-WebForms-Controls/Grid-View/Concepts/Data-Shaping-and-Manipulation/Filtering/Filter-Row">FilterRow</a> in it. Handle the <a href="https://documentation.devexpress.com/AspNet/DevExpress.Web.ASPxDataWebControlBase.DataBound.event">DataBound</a> event on the first page loading to bind BootstrapChart data to ASPxGridView data.<br>Use the <a href="https://documentation.devexpress.com/AspNet/DevExpress.Web.ASPxGridView.VisibleRowCount.property">VisibleRowCount</a> property to determine what ASPxGridView data is not filtered.<br><br>Then, handle ASPxGridView's <a href="https://documentation.devexpress.com/AspNet/DevExpress.Web.ASPxGridView.AfterPerformCallback.event">AfterPerformCallback</a> event to get filtered or sorted ASPxGridView's data and convert it to BootstrapChart's data format on the server side after a callback. In this event handler, check the <a href="https://documentation.devexpress.com/AspNet/DevExpress.Web.ASPxGridAfterPerformCallbackEventArgs.CallbackName.property">e.CallbackName</a> property to determine the sorting ("APPLYCOLUMNFILTER") or filtering ("SORT") <a href="https://documentation.devexpress.com/AspNet/DevExpress.Web.Scripts.ASPxClientBeginCallbackEventArgs.command.property">callback command</a>. Convert BootstrapChart data into the JSON format using the <a href="https://msdn.microsoft.com/en-us/library/system.web.script.serialization.javascriptserializer%28v=vs.110%29.aspx">JavaScriptSerializer</a>.<a href="https://msdn.microsoft.com/en-us/library/bb292287%28v=vs.110%29.aspx">Serialize</a> function. Set the obtained JSON data string as ASPxGridView <a href="https://documentation.devexpress.com/AspNet/11816/How-to-Access-Server-Data-on-the-Client-Side">JSProperties</a> to transfer data from the server to the client.<br><br>Handle ASPxGridView's client-side <a href="https://documentation.devexpress.com/AspNet/DevExpress.Web.Scripts.ASPxClientGridView.EndCallback.event">EndCallback</a> event for client-side data binding on a callback initiated by data filtering or sorting. Call the <a href="https://www.w3schools.com/js/js_json_parse.asp">JSON.parse</a> function to obtain transferred ASPxGridView data as a JavaScript object.<br><br>To set BootstrapChart's data source on the client side, use BootstrapChart’s private <strong>BootstrapClientChart.SetDataSource</strong> method.</p>

<br/>


