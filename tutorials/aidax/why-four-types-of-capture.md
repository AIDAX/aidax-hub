[![AIDAX logo](https://raw.githubusercontent.com/astfarias/aidax/master/files/img/logo/logo2-less.png)](http://aidaxbi.com/) 
## Why Four Types of Capture and How Use  

Different types of capture remove user-AIDAX responsibility to prevent the registration of the same event multiple times.  
We identify instances where the user wants to track a goal/target per visitor/session, so we created these and other possibilities.  

AIDAX provides four types of capture:  

- [Goal](https://github.com/AIDAX/aidax/blob/master/tutorials/aidax/why-four-types-of-capture.md#goal)
- [Attribute](https://github.com/AIDAX/aidax/blob/master/tutorials/aidax/why-four-types-of-capture.md#attribute)
- [Event](https://github.com/AIDAX/aidax/blob/master/tutorials/aidax/why-four-types-of-capture.md#event)
- [Transaction](https://github.com/AIDAX/aidax/blob/master/tutorials/aidax/why-four-types-of-capture.md#transaction)


Let's talk about each one and show how to use.

----------
### Goal 

**Goal** track visitor actions. This action may be the completion of a task, a subscription or visit a session page as the Checkout page. All that can be considered a "goal".   

Goals can be recorded once a **Visitor** or once per **Session**.    
>**Note:**  
>
> - What differentiates syntactically is the value of last attribute: Visitor (`true`), Session (`false`)   
> - Successive recordings overwrite the current value    


#### Visitor Goal  

You can see the Visitors Goals as task completed by the visitor. As an email subscription.   

```javascript
//Email Subscription
ax.goal("subscription", true, true);
```

#### Session Goal  
You can see the Visitors Goals as checkpoints completed by the visitor. As the arrival the Checkout page.   

```javascript
//Submit form of Checkout
ax.goal("submit_checkout_form", true, false);
```
----------
### Attribute  

Attributes are visitor properties, such as their name and gender.  

```javascript
//Attributing gender to visitor
ax.identify({gender: "M"});
```
>**Note:**  
>
> - The attributes are linked to the current visitor, successive recordings subscribe the current value   

----------
### Event  
Event is an case not necessarily performed by the visitor and can be accounted. As a page view.   
```javascript
//Event of page viewed 
ax.track("pageview",{title: "Home"});
```
>**Note:**  
>
> - Events can not be updated, are "fire-and-forget"   
> - It can be inserted several times  

----------
### Transaction  

Transaction is a specialized event. Its main differences are the possibility of update and context to facilitate targeting. For this, the totals transaction are recorded as visitor attribute also transaction status storage.    
```javascript
//Transaction of a Kit-Kat ($2.50)
ax.charge(2.50, true, { name: "Kit-Kat", $tags: "candy"});
```
>**Note:**  
>
> - Transaction can be updated
> - It can be inserted several times

----------
## Considerations  

 1. The types are abstractions that depend on the need and interpretation of AIDAX user.  
 2. Everything is linked to the current visitor either anonymous or identified by email, SSN, ID number, or any other identifier.
 3. If the visitor is anonymous in a system tracked by AIDAX, and is identified in some way, our algorithm will link all the information captured until the point (*Attributes, Events, Objectives* and *Transactions*) to this new identification.
 4. If the visitor was identified with a previous ID and is identified with a new ID, "*Events, Objectives* and *Transactions*" of the current session will be imported into the new ID.
 5. If ID is a email, the AIDAX user can use our Actionable Analytics using Webhook.

    
#### Standard Information Captured  

- Geolocation
- Weather forecast based on geo-coordinates
- UTM - Campaign Parameters 
- HTTP referer in session
- Device used to access
 - Browser
 - IP
 - Language
 - Operational System
 - Resolution
 
> Note
>
 - Captured information even if it is anonymous visitor  
 - All this information is also available for targeting in metric and profiles  

If you want to know how our system works under the hood, visit [Project session.](https://github.com/AIDAX/aidax/wiki/Project)

----------
## References  

[Full AIDAX Documentation](http://doc.aidax.com.br/)  
