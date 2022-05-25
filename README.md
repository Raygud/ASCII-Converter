# UTF-8-ASCII-Converter-Js

## Line 81 - Check if string is spaced by +(or what ever you need)
```javascript
if (ToDecipher.includes("+")) {
        ToDecipher = ToDecipher.split("+").join(" ")
    }
```
If the string is indeed spaced by + replace + by whitespace

# Decoder
```javascript
for (let i = 0; i < ToDecipher.length; i++) {
        if (ToDecipher[i] == "%") {
            for (let q = 0; q < ASCII.length; q++) {
                if (ASCII[q].Code == ToDecipher.substr(i, 6)) {
                    console.log(`Eureka! We found a ASCCI code : ${ToDecipher.substr(i, 6)}`)
                    let indexInASCII = ASCII.map(object => object.Code).indexOf(ToDecipher.substr(i, 6));
                    console.log(indexInASCII)
                    console.log(`Character to replace:${ASCII[indexInASCII].Code} --> ${ASCII[indexInASCII].Char}`)
                    NewString = ToDecipher.split(ASCII[indexInASCII].Code).join(ASCII[indexInASCII].Char)
                    ToDecipher = NewString
                    console.log("New String = ", NewString)

                }
            }
        }
```
Increment trough string and check if character at index is equal to "%" if this statement is true then look 6 characters ahead including "%".(Length of ASCII code is 6), check if this combinations of characters is equal to an ASCII code(we do this by looping trough our array of objects). after we have confirmed that our code does infact exsist we can find its objects index in the array using .map, after finding the index we can request the relevant Character attached to that code.
we can now construct our new string we do this by calling the split function this lets us replace any section that matches the value we but into our split function. so we can say if the string contains 123 i.e. "Hello 123 im a string 123" we can call .split("123") and then we call join to replace the value .join("New Value") = Hello New Value im a string New Value".


# Encoder
```javascript
for (let i = 0; i < ToDecipher.length; i++) {
        for (let q = 0; q < ASCII.length; q++) {
            if (ASCII[q].Char.includes(ToDecipher[i])) {
                console.log(`Eureka! We found a letter : ${ToDecipher[i]}`)
                let indexInASCII = ASCII.map(object => object.Char).indexOf(ToDecipher[i]);
                console.log(indexInASCII)
                console.log(`Character to replace:${ASCII[indexInASCII].Char} --> ${ASCII[indexInASCII].Code}`)
                NewString = ToDecipher.split(ASCII[indexInASCII].Char).join(ASCII[indexInASCII].Code)
                ToDecipher = NewString
                console.log("New String = ", NewString)
            }
        }
    }
```

This one works in a similar manner to the first function i just had to work "Backwards" i had to make a few tweaks since we are looking for singular letters this time. so we start by looping trough our string and checking if any of our characters exist inside one of the ASCII objects, when we do confirm that the character exists in the the array of objects we just flip the code from our previous function before it was 
```javascript 
let indexInASCII = ASCII.map(object => object.Code).indexOf(ToDecipher.substr(i, 6));
```
 and now we are simply swapping out object.Code with object.Char and Character code(ToDecipher.substr(i, 6)) with ToDecipher[i](letter from string) = 
```javascript
let indexInASCII = ASCII.map(object => object.Char).indexOf(ToDecipher[i]);```
