# Display texts

```python
import streamlit as st 

# Working with and Displaying Text 
st.text("Hello World this is a text")
name = "Johnny"
st.text("This is so {}".format(name))

# Title
st.title("This is a title")

# Header
st.header("This is a header")

# Subheader
st.subheader("This is a subheader")

# Markdown
st.markdown("## This is markdown")

# LaTeX
st.latex(r''' a+a r^1+a r^2+a r^3 ''')
st.latex(r'''
     a + ar + a r^2 + a r^3 + \cdots + a r^{n-1} =
     \sum_{k=0}^{n-1} ar^k =
     a \left(\frac{1-r^{n}}{1-r}\right)
     ''')
     
# Caption used for captions, asides, footnotes, sidenotes, and other explanatory text.
st.caption("this is the caption")

# Code
st.code("x=2021")

code = '''def hello():
     print("Hello, Streamlit!")'''
st.code(code, language='python')

# Displaying Colored Text/Bootstraps Alert
st.success("Successful")
st.warning("This is danger")
st.info("This is information")
st.error("This is an error")
st.exception("This is an exception")

# Superfunction
st.write("Normal Text")
st.write("## This is a markdown text")
st.write(1+2)

st.write(dir(st))

# Help Info
st.help(range)
```

!!! info "Reference and related articles"
    - :ledger: [Text elements](https://docs.streamlit.io/library/api-reference/text)
    - :ledger: [Python Tutorial: Streamlit](https://www.datacamp.com/tutorial/streamlit#3-how-to-use-streamlit)
