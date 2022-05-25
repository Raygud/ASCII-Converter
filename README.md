# Faroese-letter-Decoder-Encoder

## Line 81 - Check if string is spaced by +(or what ever you need)
```
if (ToDecipher.includes("+")) {
        ToDecipher = ToDecipher.split("+").join(" ")
    }
```
If the string is indeed spaced by + replace + by whitespace

## Line 85 - Check if string containts "%"(Start of ASCII code)
```
for (let i = 0; i < ToDecipher.length; i++) {
        if (ToDecipher[i] == "%") {
            for (let q = 0; q < ASCII.length; q++) {
                if (ASCII[q].Code.includes(ToDecipher.substr(i, 6))) {
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
