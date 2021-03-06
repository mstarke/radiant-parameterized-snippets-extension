# Radiant 'Parameterized Snippets' Extension

Call snippets with parameters which can be reused in the snippet.


## Installation

Add the following line to your Gemfile

    gem "radiant-parameterized_snippets-extension", "~> 1.0.1"

And update the bundle

    bundel update

You're good to go, since there is no need for any migrations or updates

## Usage

In some page:

What's up with elephants?
  
  <r:snippet name="animal_info" animal="elephant" />
  
And lions? What do lions do?
  
  <r:snippet name="animal_info" animal="lion" />

In snippet 'animal_info':

```xml
<r:unless_var name="animal">
  What animal do you want info about?
  Please set the 'animal' parameter when calling this snippet!
</r:unless_var>
<r:if_var name="animal">
  <r:if_var name="animal" matches=".*cat.*">
    So you wanna know something about a cat?
    Could be a 'house cat', just a 'cat' or a 'caterpillar'...
    But it is a <r:var name="animal" />!
  </r:if_var>
  
  <r:unless_var name="animal" matches="ant|mouse|eagle">
    Glad you didn't ask about ants, mice or eagles! I don't know JACK about those animals!
  </r:if_var>
  
  Enimal? Is there an enimal? If yes, tell me what it is, 
  if no, don't you dare returning an error message! <r:var name="enimal" missing="ignore" />
</r:if_var>
```  
