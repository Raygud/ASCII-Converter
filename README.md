# UTF-8-ASCII-Converter-Js

## Line 81 - Check if string is spaced by +(or what ever you need)
```
if (ToDecipher.includes("+")) {
        ToDecipher = ToDecipher.split("+").join(" ")
    }
```
If the string is indeed spaced by + replace + by whitespace

# Decoder
```
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

