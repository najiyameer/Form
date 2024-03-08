<!DOCTYPE html>
<html>
    <style>
        input[type=text], input[type=email], select {
          width: 100%;
          padding: 12px 20px;
          margin: 8px 0;
          display: inline-block;
          border: 1px solid #ccc;
          border-radius: 4px;
          box-sizing: border-box;
        }
        
        input[type=submit] {
          width: 100%;
          background-color: rgb(128, 67, 207);
          color: rgb(10, 9, 12);
          padding: 14px 20px;
          margin: 8px 0;
          border: none;
          border-radius: 4px;
          cursor: pointer;
        }
        
        input[type=submit]:hover {
          background-color: #4caf51;
        }
        
        div {
          border-radius: 5px;
          background-color: #f2f2f2;
          padding: 20px;
        }
        </style>
<body>

<h2>Form</h2>

<form name="submit-to-google-sheet">
  <label for="name">Name:</label><br>
  <input type="text" id="name" name="Name" required placeholder="Enter Name"><br>
  
  <label for="ename">Employee Name:</label><br>
  <input type="text" id="ename" name="EmpName" required placeholder="Enter Employee Name"><br>
  
  <label for="Date">Date:</label>
  <input type="date" id="date" name="Date" required><br>
  
  <label>Mistake:</label><br>
  <textarea name="Mistake" required cols="50"></textarea>
  
  <input type="submit" name="Submit"><br>

  <span id="Success"></span>
</form>
  
  <script>
    const scriptURL = 'https://script.google.com/macros/s/AKfycbyPYnuFFYR_QxhEVysZtmQxJYesqIqRZJFkFqlm6DTkWkP4gwz9LrexGYaKpgmqe_iuew/exec';
    const form = document.forms['submit-to-google-sheet'];
    const Success = document.getElementById('Success');
    form.addEventListener('submit', e => {
      e.preventDefault();
      const formData = new FormData(form);
      fetch(scriptURL, { method: 'POST', body: formData })
        .then(response => {
           Success.innerHTML = "Data Successfully Submitted";

           setTimeout(function()
           {
            Success.innerHTML = "";

           },1000)
           form.reset();
        })
        .catch(error => console.error('Error!', error.message));
    });
  </script>
</body>
</html>
