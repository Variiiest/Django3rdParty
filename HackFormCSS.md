```  
<script>

               window.onload= function(){
             document.getElementById('id_username').className+="w-full bg-gray-800 rounded border border-gray-700 text-white focus:outline-none focus:border-indigo-500 text-base px-4 py-2";
             document.getElementById('id_password').className+="w-full bg-gray-800 rounded border border-gray-700 text-white focus:outline-none focus:border-indigo-500 text-base px-4 py-2";
               }
           </script>
      
            <form action="" method="POST">
                {%csrf_token%}
                  <div>
                    <label class="block text-sm text-gray-700 mb-2">Userame</label>
                   {{form.username}}
                  </div>
                  <div>
                    <label class="block text-sm text-gray-700 mb-2 mt-2">Password</label>
                           {{form.password}}
                  </div>
           
  
                <button
                  class="block w-full px-4 py-2 mt-4 text-sm font-medium leading-5 text-center text-white transition-colors duration-150 bg-purple-600 border border-transparent rounded-lg active:bg-purple-600 hover:bg-purple-700 focus:outline-none focus:shadow-outline-purple"
                  type="submit" value="submit">Submit</button>
  
              </form>
```
