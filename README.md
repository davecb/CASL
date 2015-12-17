# CASL
CASL in pseudo-code (CASL is the Canadian anti-spam law)

You need 
- an email program whose list of customers is in a database,
- a web-site with a login
- a document with your terms and conditions

To the Terms and Conditions, add a paragraph about
sending commercial email and announcements. This is the hard part,
so you may need to seek legal advice.

To the database, add two columns
- one is TandCChangeDate and has one record, containing today's date
- the other is AgreedToTandCDate, and for each customer contains the
  date they agrred to the Terms and Conditions. This will
  initially be set to some time in the far past, "day zero" in 
  whatever date scheme the database uses

To the end of the web-site login program, add 
```
   if (TandCChangeDate is newer than thisCustomer's AgreedToTandCDate) {
        display T&C page
        ask if they agree
        if they agree {
        	set thisCustomer.AgreedToTandCDate = today
        	complete login
        }
        else, if they do not agree {
        	return them to the "please log in" page
        }
    } 
```

If your email program or web site is from a vendor, ask if they already
have this feature.  One of my customers already did, so we only needed
to update the T&Cs and change the TandCChangeDate.
