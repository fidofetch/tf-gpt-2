# tf-gpt-2

Java library for the GPT-2 Text Model using Tensorflow

Source:
1. [Original Python Release](https://github.com/openai/gpt-2)
1. [OpenAI Blog - GPT2 Details](https://openai.com/blog/better-language-models/)

More Background:
1. [Transformers and Attention Models](http://jalammar.github.io/illustrated-transformer/)

## Basic Usage

### Import the Original Library

```xml
<dependency>
    <groupId>com.simiacryptus</groupId>
    <artifactId>tf-gpt-2</artifactId>
    <version>2.0.0</version>
</dependency>
```

### Solution to InvalidGraphDef

The workaround I've found to work is to go to https://s3-us-west-2.amazonaws.com/simiacryptus/gpt2/345M.pb
Replace the 345M.pb in your project folder with the 1.3gb file.

### Instantiate the text generator

```java
import com.simiacryptus.text.TextGenerator;
import com.simiacryptus.text.gpt2.GPT2Util;
TextGenerator textGenerator = GPT2Util.get345M();
```

### Generate text

```java
System.out.println(textGenerator.generateText(500));
```

### Generate text given prefix

```java
System.out.println(textGenerator.generateText(500, "Once upon a time"));
```

### Generate text that continues from previous output

As of right now generateText() will reset the state and history.
Use generate() to maintain state and feed() to input without losing state.

```java
System.out.println(textGenerator.generate(500);
```
