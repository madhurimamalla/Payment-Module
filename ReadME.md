<h3> Steps to run this project: </h3>
- Install a tomcat server and place this in its webapp's folder
- Start the tomcat server
- Open a browser and hit http://localhost:8080/Payment-Module/ OR http://127.0.0.1:8080/Payment-Module/
- It will now load the index.html 

<h3>Description:</h3>
<p>The index.html page loads the Order Summary page in the module. This order summary details are populated from the data in orderDetails.json. One can add more data to the orderDetails.json and see how it gets updated on the Order Summary page. Once the items are verified one can proceed by clicking "Proceed to Payment" which then takes one to the Payment Methods page. Here, by default the Wallet option is chosen. You can verify your order summary details one last time. The order summary gives the total payable amount including the delivery charges. If the wallet is chosen, one can check that there's enough balance in the Wallet (this is populated after getting the balance from the paymentMethods.json), enter required values and complete the payment. If one chooses to pay by Debitcard, click the Debitcard option on the left sidebar and the debitcard panel shows up. Enter the details and finish the payment. A successful transaction will show a success message. And, in other cases, it'll show a failure message.<p>

<h3>How to add another payment method?</h3>
<p>Create a javascript file, say creditcard.js and write the entire processor logic and the view logic in this file and save it in the js folder. </p>
<p>In the paymentMethods.js file, which is the where we control the logic of paymentMethods.html, add code like this:</p>
<p>Add the 'creditcard' to the dependencies in the define() and when it's done it'll look like this, ['wallet','debitcard', 'creditcard', 'order'] and the function(wallet,debitcard,creditcard,order)</p>
<p> Also, add: <br>
    <code> creditcard.init(); 
     $('#creditcard').click(function () { 
        $('#walletClick').html(creditcard.creditcardView.render().el);
        creditcard.creditcardView.bindEventListeners();
    }); </code> </p>
 <p>In the paymentMethods.html, I've already added a <code> &lt;li&gt;&lt;a href="#" id="creditcard"&gt;Credit Card&lt;/a&gt;&lt;li&gt; </code> in the sidebar for credit card option but any other method can be added with ease.
</p>
