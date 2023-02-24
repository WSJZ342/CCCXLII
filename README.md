# CCCXLII
<!DOCTYPE html>
<html>
<head>
   <title>CCCXLII</title>
   <style>
       body {
           background-color: #f1f1f1;
       }

       .container {
           width: 50%;
           margin: auto;
           padding: 20px;
           background-color: #f1f1f1;
           text-align: center;
       }

       textarea {
           margin: 10px;
       }

       button {
           margin: 10px;
       }
   </style>
</head>
<body>
   <div class="container">
       <h1>CCCXLII</h1>
       <p>Enter a message to encrypt or decrypt:</p>
       <textarea id="message" rows="5" cols="50"></textarea><br><br>
       <button onclick="encryptMessage()">Encrypt</button>
       <button onclick="decryptMessage()">Decrypt</button>
       <br><br>
       <div>
           <label for="result">Result:</label>
           <textarea id="result" rows="5" cols="50" readonly></textarea>
       </div>
   </div>
   <script src="aes.js"></script>
   <script>
       function encryptMessage() {
           var message = document.getElementById("message").value;
           var encrypted = "";
           for (var i = 0; i < message.length; i++) {
               var letter = message.charAt(i).toUpperCase();
               if (letter >= "A" && letter <= "Z") {
                   var number = letter.charCodeAt(0) - 64;
                   if (encrypted != "" && encrypted.charAt(encrypted.length - 1) != "-") {
                       encrypted += "-";
                   }
                   encrypted += number;
               } else if (letter == " ") {
                   encrypted += "/";
               }
           }
           document.getElementById("result").value = encrypted;
       }

    function decryptMessage() {
 var message = document.getElementById("message").value;
 message = message.replace(/\//g, " "); // Replace slashes with spaces
 var decrypted = "";
 var words = message.split(" ");
 for (var i = 0; i < words.length; i++) {
   var word = words[i];
   if (word == "") {
     continue;
   }
   var parts = word.split("-");
   for (var j = 0; j < parts.length; j++) {
     var part = parts[j];
     if (part == "") {
       continue;
     }
     var number = parseInt(part);
     var letter = String.fromCharCode(number + 64);
     decrypted += letter;
     if (j < parts.length - 1) {
       decrypted += "";
     }
   }
   decrypted += " ";
   if (word.endsWith(".") || word.endsWith("?") || word.endsWith("!")) {
       decrypted += "<br>";
   }
 }
 document.getElementById("result").value = decrypted;
}


    
<div id="result" style="background-color: lightgrey; width: 50%; margin: 0 auto;" contenteditable="true"></div>



        
       
   </script>
</body>
</html>
