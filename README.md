# Welcome to Agile Lab!

This is our technical test. Once you are done, you can either upload the answers to your own repository and share us the link, or you can zip your answers up and send it directly to us via email!

Enjoy!

## 1. Anagram Tester

An anagram is created by re-arranging the letters of a word. For example, the word `LISTEN` is an anagram of `SILENT`.
You can find the definition in [Wikipedia](https://en.wikipedia.org/wiki/Anagram).
Below is a skeleton defenition of a method for testing if two words make an anagram. Your task is to implement this
method, using Ruby. It should take in two strings and return `true` if the two words make an anagram, or `false` if it's not.

```ruby
def anagram?(first_word, second_word)
  # Add your implementation here
  return false if first_word.length != second_word.length
  first_word_chars = first_word.chars.sort_by(&:downcase)
  second_word_chars = second_word.chars.sort_by(&:downcase)
  first_word_chars.each_with_index{|char, i| return false if char.downcase != second_word_chars[i].downcase}
  return true
end
```

**Rules:**
 - You don't need to care about upper- and lowercase letters. That is, `A` and `a` can be considered the same for the purposes of this test.
 - You only need to care about single words. The method does not need to handle sentences.
 
 
## 2. Anonymous Chat

You are tasked to create a Anonymous Chat where public is able to initiate a anonymous conversation with the admin

You are to only required to create the `routes.rb` that can fulfil all the requirements listed below.

```ruby
# config/routes.rb
Rails.application.routes.draw do
  # Add your routes for Anonymous Chat

  post '/conversations', to: 'conversations#create' # initiate the chat
  get '/conversations/:id/messages', to: 'messages#index' # get messages by chat(conversations)
  post '/conversations/:id/messages', to: 'messages#create' # Public sent message

  scope :admin do
    put '/conversations/:id/mark_seen', to: 'conversations#mark_seen' # mark the chat that admin seen it
    get '/conversations', to: 'conversations#index' # get all chat
    get '/conversations/:id/messages', to: 'messages#index' # get messages by chat(conversations)
    post '/conversations/:id/messages', to: 'messages#create' # admin response to the chat
    put '/conversations/:id/closed', to: 'conversations#closed' # admin closed the conversation.
  end
end
```

**Requirements:**
 - Public can initiate the chat
 - Admin can acknowledge that they have seen the chat (not messages).
 - Admin can response to the chat with the person who initiate the chat.
 - Admin can closed the conversation.
 - Admin cannot initiate the chat.


## 3. Bug Fixing

When client or users reported an issue to you, describe what you do next.
How do you go about trouble shooting the issue? Depending on what you find, what will your next step be? When do you
consider the issue fixed or resolved?

**Tips:**
- You are free to make **ANY** assumptions, write down your assumptions.

**My solution:**
- First I will check in monitor system to find any errors that related this issue, if not I will ask client/user how to reproduce this bug
- To trouble shooting the issue I will check those inputs from user/client and log system to know the cause of the issue
- I will fix/test this bug in local eviroment, then I will deploy and testing in develop, and asking QA to check this issue and related feature can side effect.
- if QA confirm everything is OK, I will deploy it in production
- I consider the issue fixed or resolved when client/user confrim this issue has gone.
## 4. Taking over an old project

You have recently been assigned to an old project, the previous developer had already left and you are tasked to take over the project and implement new features.
However you are facing some problems, the new feature that you are implementating doesn't seem to go well with the existing features.
The more you code, the more edge case you encounter.

Describe, in as much detail as you like, how you would handle this situation.

**Tips:**
- You are free to make **ANY** assumptions, write down your assumptions.

**My solution:**
- Fail-safe: We will run 2 app, old app for old features and new app for new feature
- We need to double-check with new features
- In the long-run, We need write full test case for old features and then we can continue develop new feature in old app
