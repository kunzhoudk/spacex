# Streamlit Widget

## Working with Buttons

```python
name = "Jesse"
if st.button("Submit"):
    st.write("Name: {}".format(name.upper()))
```

If you have multiple buttons, then you can use "key" attribute to give a unique name for each button 

```python
if st.button("Submit", key='new02'):
    st.write("First Name: {}".format(name.lower()))
```

To invoke a function when click on a button 

```python
if 'count' not in st.session_state:
    st.session_state.count = 0

def increment_counter():
    st.session_state.count += 1

st.button('Increment', on_click=increment_counter)

st.write('You clicked to increment count, total count = ',
         st.session_state.count)
```

## Working with RadioButtons

```python
status = st.radio("What is your status", ("Active", "Inactive"))
if status == 'Active':
    st.success("You are active")
elif status == "Inactive":
    st.warning("Inactive")

city_options = {
    5: "Arizona - Chandler - 5",
    4: "Arizona - Phoenix - 4",
    3: "New Jersey - Newark -3",
    2: "Oregon - Portland - 2",
    1: "Seattle - Washington - 1",
}

city_mode = st.sidebar.radio(
    label="Choose a city option:",
    options=(5, 4, 3, 2, 1),
    format_func=lambda x: city_options.get(x),
)

st.write(f'You have chosen {city_options.get(city_mode)}'
         f' with the value {city_mode}.')
```

## Working with Checkbox

```python
if st.checkbox("Show/Hide"):
    st.text("Showing something")
```

## Working with Expander

```python
if st.expander("Python"):
    st.success("Hello Python")

with st.expander("Julia"):
    st.text("hello Julia")
```

## Working with one select

```python
my_lang = ["Python","Julia","Go","Rust"]
choice = st.selectbox("Language",my_lang)
st.write("You selected {}".format(choice))
```

## Working with multiple select

```python
spoken_lang = ("English","French","Spanish","Twi")
my_spoken_lang = st.multiselect("Spoken Lang",spoken_lang,default="English")
```

## Working with slider 

The difference between `st.slider` and `st.select_slider` is that slider only accepts numerical or date/time data and takes a range as input, while select_slider accepts any datatype and takes an iterable set of options.
 
* Numbers (Int/Float/Dates)
    ```python  
    age = st.slider("Age", 1, 100)
    st.write("age:", age)
    ```
* Any Datatype using Select Slider
    ```python  
    color = st.select_slider("Choose Color", options=["yellow", "red", "blue", "black", "white"], value=("yellow", "red"))
    st.write("color:", color)
    ```
