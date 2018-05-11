# ESP8266-base64

These are functions to encode and decode data to and from the Base64 format.

The original code is from this github repository: https://github.com/AxisCommunications/arduino-websocket-server/blob/master/Base64.cpp.

## API:

There are two functions: one for encode and one for decode:

 int encoded_lenght = b64_encode( char *data_out, char *data_in, int data_in_lenght );

 int decoded_lenght = b64_decode( char *data_out, char *data_in, int data_in_lenght );


## How to use:

 I've used the Sming framework for the ESP8266, but the code should be portable to other architectures and frameworks:

### Encoding:
    char b64data[256];   // Size is just an example.
    String s = "Hello world!";
    Serial.println(" Message: " );
    Serial.println( s) ;    
    
    Serial.println(" Encoded message:");
    int b64len = b64_encode(b64data, (char *)s.c_str(),s.length());
    Serial.println ( String(b64data) );
    Serial.println ("The lenght is: " + String(b64len) );


### Decoding:
    char decoded[256];
    String ss(b64data);
    b64_decode( decoded , (char *)ss.c_str() , ss.length() );
    Serial.println("Decoded: " + String(decoded));

 or

    b64_decode( decodec, b64data, b64len);
    Serial.println("Decoded: " + String(decoded));
