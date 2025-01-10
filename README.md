# tiktoken-go
OpenAI's tiktoken in Go. 

Tiktoken is a fast BPE tokeniser for use with OpenAI's models.

This is a port of the original [tiktoken](https://github.com/openai/tiktoken).  

# Usage
## Install

```bash
go get github.com/herta-witch/tiktoken-go
```

## Addition Features
 - Whisper's tokenizer
 - Handle invalid base64 string in .tiktoken file

## Examples
### Get Token By Encoding

```go
package main

import (
    "fmt"
    "github.com/herta-witch/tiktoken-go"
)

func main()  {
	tiktokenFileName := "multilingual"
	numLanguages := 100
	encodingDir := "./"

	tke, err := GetWhisperEncoding("multilingual", 100, "./")
	if err != nil {
		err = fmt.Errorf("getEncoding: %v", err)
		return
	}

	prompts := "<|startoftranscript|><|th|><|transcribe|><|notimestamps|>"

	token := tke.Encode(prompts, []string{"all"}, nil)

	fmt.Printf("token: %v, length: %d\n", token, len(token))
}
```

# License
[MIT](./LICENSE)
