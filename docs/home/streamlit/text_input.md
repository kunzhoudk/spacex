# Text Inputs

## Single-line text input widget

```python
fname = st.text_input("Enter Firstname")
```

## Text Input Hide Password

```python
password = st.text_input("Enter Password",type='password')
st.title(fname)
```

## A multi-line text input widget

```python
message = st.text_area("Enter Message",height=100)
st.write(message)
```

## Numbers

```python
number = st.number_input("Enter Number",1.0,25.0)
```

## Date Input

```python
myappointment = st.date_input("Appointment")
```

## Time Input

```python
mytime = st.time_input("My Time")
```

## Color Picker

```python
color = st.color_picker("Select Color")
```
