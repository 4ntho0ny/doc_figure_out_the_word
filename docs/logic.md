# Programming Logic of the game

All the programmig logic of the game be in the app `game/` in file `views.py`.

The `views.py` have some functions, which are the logic of game. The functions is listed below:

## get_word_list()

This function access [api-imersao-ia](https://raw.githubusercontent.com/guilhermeonrails/api-imersao-ia/main/words.json), 
an api with several words and hints of technology world.

Its return a list of dictionaries. Each dictionary contain a word and a hint.

## random_word()

Receive [get_word_list()](#get_word_list) and store in **list_objects** variable. After, this function return only one dictionary drawed for [random.choice(list_objects)](https://docs.python.org/3/library/random.html#functions-for-sequences).

## starting_page(request)

Render the [starting_page.html](http://localhost:8000/#start-page). Is used [render](https://docs.djangoproject.com/en/5.1/topics/http/shortcuts/#render) method.

## validate_answer(form)

When we are into [game page](http://localhost:8000/#game-page), a form with answer field is avaliabe, where we'll fill with some word.
This form will be validated by validate_answer(). If word is correct, return **True**, else **False**.

The correct answer and hint is a fields with [`display: none`](https://www.w3schools.com/css/css_display_visibility.asp). When subtmited the forms, send these two fields and the word typed for player.

```py title="views.py"
def validate_answer(form):
    if form.is_valid():
        word = form.cleaned_data["word"].lower().strip()
        correct_answer = form.cleaned_data["correct_word"].lower()
    
        if word == correct_answer:
            return True
        else:
            return False
```

## play_page(request)

The `play_page(request)` is a most important method of the game. This can receive two request methods: **GET** and **POST**

* ### request.method == "GET"



* ### request.method == "POST"