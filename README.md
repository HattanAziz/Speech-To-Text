# Speech-To-Text
How to Convert Audio to Text with HTML , JS , CSS



...


<!doctype html>
	<head>
		<style>
		
			body {
			   
              font-size: 30px;
             margin: 0%;
              background: linear-gradient(to right bottom,#a7f3da,#a7f3da);
              display: list-item;
               align-items: safe center;
               justify-content:space-evenly;
                min-height: 100vh;
               color:rgb(30, 36, 24);
              }
			
			button {
			  
				background: #34a9bb;
               border: 2px solid #555555;   
               border-radius: 20px;
			   box-shadow: 0 8px 16px 0 rgba(0,0,0,0.2), 0 6px 20px 0 rgba(0,0,0,0.19);
			   font-size: 24px;
			   width: 100%;
			   padding: 1px 6px;
               cursor: pointer;
            color: rgb(150, 22, 22);
			}
			#output {
			    background-color:#fdfcff;
			    padding:10px;
			    width: 100%;
			    margin-top:20px;
			    line-height:60px;
			}
			.hide {
			    display:none;
			}
			.show {
			    display:block;
			}
		</style>
		<title> Speech to Text</title>
	</head>
	<body>
		<h2> Speech to Text</h2>
        <p>Click the button...</p>
        <p><button type="button" onclick="runSpeechRecognition()">Start</button> &nbsp; <span id="action"></span></p>
        <div id="output" class="hide"></div>
		<script>
			
		    function runSpeechRecognition() {
		        
		        var output = document.getElementById("output");
		      
		        var action = document.getElementById("action");
                
                var SpeechRecognition = SpeechRecognition || webkitSpeechRecognition;
                var recognition = new SpeechRecognition();
				recognition.lang="ar";
            
                
                recognition.onstart = function() { //بعد ما تضغط على ابدا يتغير 
                    action.innerHTML = "<small> please speak...</small>";
                };
                
                recognition.onspeechend = function() {
                    action.innerHTML = "<small> listening stopped...</small>";
                    recognition.stop();
                }
              
                
                recognition.onresult = function(event) {
                    var transcript = event.results[0][0].transcript;
                    output.innerHTML = "<b>The text on Arabic: </b> " + transcript ;
                    output.classList.remove("hide");
                };
              
                 
                 recognition.start();
	        }
		</script>
	</body>
</html>
...
