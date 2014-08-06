postJSONKo
==========

The goal is to solve a bug. To send data via post, if the data contains the following sequence of characters: "??". The error has been described on the following link for other users. http://bugs.jquery.com/ticket/12326

##What this?
PostJSONKo is function Konockoutjs

##Keyworks
jQuery, Post, Knockoutjs, ??

##Example of use

Add:
```javascript
ko.computed.fn.postJSONKo = function(object) {
	var data = ko.toJSON(object);
	return data.replace("??","?\\?");
}
```

And

```javascript
$.ajax({
    type: "POST",
    url: url,
    dataType: 'json',
    data: ko.computed.fn.postJSONKo(self.object()),
    beforeSend: function (request) {
        request.setRequestHeader('Content-Type', "application/json; charset=utf-8")
    },
    success: function (return) {
        
    },
    error: function (err) {
        console.log(err.status + " - " + err.statusText);
    }
});
```

________________________________________
2014 - Márcio Vinícius Oliveira Sena (@marciovsena)
