# -toastmessagein-html
Its very simple to create atoast message like android on website
function valiadteLogin() {
           var msg = "is required", errCount = 0;
           var pwd = $("#pwd");
           var email = $("#email");
           
           if (email.val() == "") {
              obj = email;
              msgObj = "Email "+ msg;
              errCount ++;
           }
           else if (checkemail(email.val()) === false) {
              obj = email;
              msgObj = "Please enter valid email";
              errCount ++;
           }
            else if (pwd.val() == "") {
              obj = pwd;
              msgObj = "Password "+ msg;
              errCount ++;
           }
           
           if (errCount > 0) {
              CreateToast(msgObj);
              //obj.focus();
              return false;
           }else
           {
              return true;
           }
       }
/*
*Validation message popup
*/
function CreateToast(messageArg) {
   //alert($(window).height());
  $('body').find('.ToastMsg').remove();
  ToastMsg = "<div class='ToastMsg' onclick='ToastDismiss(this.id)' id='ToastMsg'><span>"+messageArg+"</span></div>";
  $('body').append(ToastMsg);
  var MsgWidth = $('#ToastMsg span').width();
  $('#ToastMsg').width(MsgWidth);
  setTimeout(function(){ToastDismiss('ToastMsg')},5000);
}
function ToastDismiss(args) {
  $('#'+args).remove();
}
/*
/*
*Toast Message
*/
div#ToastMsg.ToastMsg{position: fixed;bottom: 10px;background: rgba(0, 0, 0, 0.68);padding: 10px 20px;left: 0;right: 0;margin: 0 auto;width: auto;text-align: center;color: #fff;border-radius: 25px;}
div#ToastMsg.ToastMsg span{margin-bottom: 0;}
