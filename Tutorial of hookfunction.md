# hookfunction lua tutorial - full guide

## This is the ultimate guide to hookfunction in Lua, explaining how it works, how to use it effectively, and real examples!


---

# What is hookfunction?

# hookfunction is a powerful function used in Lua executors (mainly in Roblox) that allows you to override or modify existing functions at runtime.

# By using hookfunction, you can:
## Modify game functions without changing the source code.
## Redirect function calls to custom functions.
## Intercept and log data before returning original results.


---

# Basic Syntax of hookfunction

### The syntax is straightforward:

### local old_function = hookfunction(target_function, new_function)

### target_function: The original function you want to modify.

### new_function: Your custom function that replaces the original.

### old_function: Stores the original function (so you can call it if needed).



---

# Example 1: Hooking print() Function

modify print() to add [HOOKED] before every message!
```Lua
local old_print = hookfunction(print, function(...)
    old_print("[HOOKED] ", ...)
end)

print("Hello, world!") -- Output: [HOOKED] Hello, world!
```
This replaces the normal print() with a hooked version that adds a prefix.


---

# Example 2: Hooking a Game Function (Roblox)

hook game.HttpGet() to prevent HTTP requests:
```Lua
local old_HttpGet = hookfunction(game.HttpGet, function(self, url, ...)
    print("Blocked request to: " .. url)
    return old_HttpGet(self, "https://safe-url.com", ...) -- Redirect to a safe URL
end)
```
If a script tries to call game:HttpGet("https://example.com"), it gets blocked or redirected!



---

# Example 3: Hooking to Modify Game Behavior

change math.random() so it always returns 100:
```Lua
local old_random = hookfunction(math.random, function(...)
    return 100
end)

print(math.random(1, 10)) -- Output: 100
```
This overrides math.random() so no matter the input, it always returns 100.



---

# Example 4: Hooking a GUI Function in Roblox

modify TextLabel.Text so it always displays "modified!"
```Lua
local old_setText = hookfunction(game.TextLabel.SetText, function(self, text)
    return old_setText(self, "modified!") -- Force text to be "modified!"
end)
```
Any time a script sets a TextLabel's text, it gets changed!



---

# Example 5: Restoring the Original Function

If you ever need to restore the original function, just call old_function:
```Lua
hookfunction(print, old_print) -- Restore the original print function
print("This is back to normal!") -- Output: This is back to normal!
```

---

### When to Use hookfunction?

Modifying built-in functions in Lua.
Overriding game functions in Roblox/FiveM.
Logging or blocking specific function calls.
Redirecting or manipulating function outputs.


---

# Important Notes

hookfunction is only available in some Lua executors (e.g., Roblox exploits).

It does NOT exist in normal Lua (like vanilla Lua 5.1 or LuaJIT).

Always store the original function (old_function) in case you need to restore it.



---

# CONCLUSION: master hookfunction, scripter exploit and happy coding!

### With this tutorial, you now fully understand hookfunction and how to use it to modify Lua scripts dynamically, tutorial by ScripterMrbacon
