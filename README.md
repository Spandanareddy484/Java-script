# Java-script
//Acceptance Criteria:
//Name = "Carbon credits"
//CanRelist = true
//The Promotions element with Name = "Gallery" has a Description that contains the text "Good position in category"
        
    
    //Successful GET request
    pm.test("Successful GET request", function () {
    pm.expect(pm.response.code).to.be.oneOf([200,201,202]);
    });

    //Status code is 200
    pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
    });

    // Name = "Carbon credits"
    pm.test("Name = 'Carbon credits'", function () {
    pm.expect(pm.response.text('Name'))
    .to.include("Carbon credits");
    });

   // CanRelist = true // text test
    pm.test("CanRelist = true // text test", function () {
    pm.expect(pm.response.text('CanRelist'))
    .to.include("true");
    });

  // CanRelist = true // boolean test
    pm.test("CanRelist = true //boolean test", function () {
    var jsonData = pm.response.json();   
    pm.expect(jsonData.CanRelist).to.be.true;
    });


  // The Promotions element with Name = "Gallery" has a Description that contains the text "Good position in category"
    pm.test("Promotions element with Name = 'Gallery' has a Description that contains the text 'Good position in category'", function () {
    var body = JSON.parse(responseBody);
       for (var i = 0;i<body.Promotions.length; i++) {
       if (body.Promotions[i].Name === 'Gallery') 
       {
        pm.expect(body.Promotions[i].Name).to.eql('Gallery');
        pm.expect(body.Promotions[i].Description).to.include ('Good position in category'); 
       }
       }
});
