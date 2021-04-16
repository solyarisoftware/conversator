# Conversator

Chat bot conversations *router*:  framework to connect users to operators (*humans* or *bots*).

NOTE: This is just a DRAFT readme/manifesto**.

## Motivation / Goal

Working around conversational commerce messaging apps, and specifically thinking about a chat bots on the [telegram](http://www.telegram.org) instant messaging platform, I faced with a typical call center/help desk/customer care task: **to route incoming customers requests to a chat bot to a pool of operators**.

![](https://upload.wikimedia.org/wikipedia/commons/e/e0/Telephony_multiplexer_system.gif)

The gist here is to realize a bot framework that act as *multiplexer/demultiplexer* routing incoming users/customers requests to some **operators, that could be or humans or bots applications (NLP-enabled to converstate with users)**.

This is useful for a standard customer care scenario: customers contact a *contact center* (realized here through a Telegram bot account) to talk with an operator, to have any sort of *service*: getting some info, or to solve an issue with the help pf an expert (see healthcare assistance/patient monitoring), or to purchase something (conversational ecommerce).

A bot act as a front-end to customers, 
* verifying id user is new, or retrieving his previous *session data*
* dispatching the incoming *messaging call* to a *back-end operator* 

The important point is: WHO is the *operator* ? 
* Operator is an Human operator
  Is really a person! A human being.
* Operator is a bot (again!)
  The bot talk with user in his natural language and the bot could substitute human operator to solve simple requests (depending on the context), chatting with user as "first level helpdesk". 

## Architecture

The multiplexing logic could be decided by an *hypervisor/scheduler* (round robin routing among available operators). Profiling  logics could be implemented easily. A profit scenario could foresee to let the user talk with a specific Person, maybe a very specilized operator, etc. etc.

Routing have to be dynamic: as soon a conversation between an user and an operator end, the operator pass from state `busy` to `free` and could converse with a new user. A human operator could decide himself to become available for a new conversation (e.g. submitting a `/start` command to the hypervisor bot), and where a conversation is concluded (e.g. submitting a `/stop` command to the hypervisor bot). Afterall, with some implicit logic, a bot operator could do the same :-). 

```
              +-----------------------------------------------+   
              |  hypervisor logic / scheduler                 | <-- HUMAN Administrator
              |                                               |       
              +-----------------------------------------------+       
                                    |  ^                              
                                    v  |                              
              +-----------------------------------------------+       
              |                                               |      
 User ------> | <---------------+         +-----------------> | <-- HUMAN Operator: Giorgio
              |                 |         |                   |        
 User ------> | <---+     +-----|---------|-----------------> | <-- HUMAN Operator: Giuditta
              |     |     |     |         |                   |       
 User ------> | <---|-----|-----|---------|-----+      +----> | <-- HUMAN Operator: Luca
              |     |     |     |         |     |      |      |       
 User ------> |     |     |     |         |     +------|----> | <-- BOT Operator (fallback)
              |     +-----|-----|---------|------------+      |       
 User ------> | <---------+     +---------|-----------------> | <-- BOT Operator (fallback)
              |                           |                   |       
 User ------> | <-------------------------+                   | <-- BOT Operator (fallback)
              |                                               |       
              +-----------------------------------------------+
```


## COMING SOON Source Code

The conversator alghorithm is pretty simple; using the Telegram Bot platform, everyone connected to a bot (specifically in this context: an *user*, an *operator*) is identified by a permenent `chat_id`. `Conversational sessions` statuses, profilings, routes data, could be stored and retrieved to implement the routing logic. 

Pseudocode:

```javascript

const chatId = message.chat_id
const text = message.text

// incoming update message from an user ?
if ( isUser(chatId) ) {

  if (activeConversation(chatId))
    forwardMessageTo(assigned_operator)
  else
    forwardMessageTo(new_operator)  

}  

// incoming update message from an operator ?
if ( isOperator(chatId) ) {
  
  if ( isCommand(text) ) {
    // operator command management (internal admins/operations), e.g. /commands
    execCommand(text)
  }  
  else {
    // forwarding message to user
    if ( activeConversation(chatId) )
      forwardMessageTo( assigned_operator )
    else
      forwardMessageTo( new_operator )  
  }
}
```


## Contact

- If you like this project, 
  - **Give a START to the project here!**, 
  - share and contribute!
  - Contact me, via email
- mail: [giorgio.robino@gmail.com](mailto:giorgio.robino@gmail.com)
- blog: [@solyarisoftware](http://www.twitter.com/solyarisoftware)

---

