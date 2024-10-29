# Compare finetuned vs. non-finetuned models


```python
import os
import lamini

lamini.api_url = os.getenv("POWERML__PRODUCTION__URL")
lamini.api_key = os.getenv("POWERML__PRODUCTION__KEY")
```


```python
from llama import BasicModelRunner
```

### Try Non-Finetuned models


```python
non_finetuned = BasicModelRunner("meta-llama/Llama-2-7b-hf")
```

    LAMINI CONFIGURATION
    {}
    LAMINI CONFIGURATION
    {}
    LAMINI CONFIGURATION
    {}



```python
non_finetuned_output = non_finetuned("Tell me how to train my dog to sit")
```


```python
print(non_finetuned_output)
```

    .
    Tell me how to train my dog to sit. I have a 10 month old puppy and I want to train him to sit. I have tried the treat method and he just sits there and looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at me like I am crazy. I have tried the "sit" command and he just looks at



```python
print(non_finetuned("What do you think of Mars?"))
```

    
    I think it's a great planet.
    I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I think it's a great planet. I



```python
print(non_finetuned("taylor swift's best friend"))
```

    
    I'm not sure if I've mentioned this before, but I'm a huge Taylor Swift fan. I've been a fan since her first album, and I've been a fan ever since. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality, and her music. I've been a fan of her music, her style, her personality



```python
print(non_finetuned("""Agent: I'm here to help you with your Amazon deliver order.
Customer: I didn't get my item
Agent: I'm sorry to hear that. Which item was it?
Customer: the blanket
Agent:"""))
```

    I'm sorry to hear that. I'll look into it.
    Customer: I'm not sure if I got the right blanket.
    Agent: I'm sorry to hear that. I'll look into it.
    Customer: I'm not sure if I got the right blanket. I'm not sure if I got the right blanket.
    Agent: I'm sorry to hear that. I'll look into it. I'll look into it.
    Customer: I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket.
    Agent: I'm sorry to hear that. I'll look into it. I'll look into it. I'll look into it.
    Customer: I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got the right blanket. I'm not sure if I got


### Compare to finetuned models 


```python
finetuned_model = BasicModelRunner("meta-llama/Llama-2-7b-chat-hf")
```

    LAMINI CONFIGURATION
    {}
    LAMINI CONFIGURATION
    {}
    LAMINI CONFIGURATION
    {}



```python
finetuned_output = finetuned_model("Tell me how to train my dog to sit")
```


```python
print(finetuned_output)
```

    on command.
    Training a dog to sit on command is a basic obedience command that can be achieved with patience, consistency, and positive reinforcement. Here's a step-by-step guide on how to train your dog to sit on command:
    
    1. Choose a quiet and distraction-free area: Find a quiet area with minimal distractions where your dog can focus on you.
    2. Have treats ready: Choose your dog's favorite treats and have them ready to use as rewards.
    3. Stand in front of your dog: Stand in front of your dog and hold a treat close to their nose.
    4. Move the treat up and back: Slowly move the treat up and back, towards your dog's tail, while saying "sit" in a calm and clear voice.
    5. Dog will sit: As you move the treat, your dog will naturally sit down to follow the treat. The moment their bottom touches the ground, say "good sit" and give them the treat.
    6. Repeat the process: Repeat steps 3-5 several times, so your dog learns to associate the command "sit" with the action of sitting.
    7. Gradually phase out the treats: As your dog becomes more comfortable with the command, start phasing out the treats. Instead, use praise and affection as rewards.
    8. Practice, practice, practice: Practice the "sit" command in different locations, with different distractions, and at different times of the day. This will help your dog understand that the command is universal and applies in all situations.
    9. Be consistent: Consistency is key when training a dog. Make sure everyone in the household is using the same command and reward system.
    10. Be patient: Training a dog takes time and patience. Don't get frustrated if your dog doesn't pick up the command immediately. Keep practicing and eventually, your dog will learn.
    
    Remember, training a dog is a journey, and it's important to be patient, consistent, and positive. With time and practice, your dog will learn to sit on command and other basic obedience commands.



```python
print(finetuned_model("[INST]Tell me how to train my dog to sit[/INST]"))
```

     Training your dog to sit is a basic obedience command that can be achieved with patience, consistency, and positive reinforcement. Here's a step-by-step guide on how to train your dog to sit:
    
    1. Choose a quiet and distraction-free area: Find a quiet area with no distractions where your dog can focus on you.
    2. Have treats ready: Choose your dog's favorite treats and have them ready to use as rewards.
    3. Stand in front of your dog: Stand in front of your dog and hold a treat close to their nose.
    4. Move the treat up and back: Slowly move the treat up and back, towards your dog's tail, while saying "sit" in a calm and clear voice.
    5. Dog will sit: As you move the treat, your dog will naturally sit down to follow the treat. The moment their bottom touches the ground, say "good sit" and give them the treat.
    6. Repeat the process: Repeat steps 3-5 several times, so your dog starts to associate the command "sit" with the action of sitting down.
    7. Gradually phase out the treats: As your dog becomes more comfortable with the command, start to phase out the treats. Instead, use praise and affection as rewards.
    8. Practice, practice, practice: Practice the "sit" command in different locations, with different distractions, and at different times of the day. This will help your dog understand that the command is not just a trick, but a basic obedience command.
    9. Be consistent: Consistency is key when training a dog. Make sure everyone in the household is using the same command and reward system.
    10. Be patient: Training a dog takes time and patience. Don't get frustrated if your dog doesn't pick up the command immediately. Keep practicing and eventually, your dog will learn.
    
    Additional tips:
    
    * Start training early: The earlier you start training your dog, the easier it will be for them to learn.
    * Use a consistent command: Choose a consistent command for "sit" and use it every time you want your dog to sit.
    * Use a gentle touch: When using the command, use a gentle touch on your dog's nose to guide them into the sitting position.
    * Be clear and concise: Use a clear and concise command, such as "sit" or "down," and avoid using long sentences or complicated words.
    * Practice in different situations: Practice the "sit" command in different situations, such as during walks, in the park, or at home, to help your dog understand that the command is not just a trick, but a basic obedience command.
    
    Remember, training a dog takes time, patience, and consistency. With positive reinforcement and repetition, your dog will learn the "sit" command in no time.



```python
print(non_finetuned("[INST]Tell me how to train my dog to sit[/INST]"))
```

    
    [INST]Tell me how to train my dog to sit[/INST]
    [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how to train my dog to sit[/INST] [INST]Tell me how



```python
print(finetuned_model("What do you think of Mars?"))
```

    
    
    Mars is a fascinating planet that has captured the imagination of humans for centuries. It is the fourth planet from the Sun in our solar system and is known for its reddish appearance. Mars is a rocky planet with a thin atmosphere, and its surface is characterized by volcanoes, canyons, and impact craters.
    
    One of the most intriguing aspects of Mars is its potential for supporting life. While there is currently no evidence of life on Mars, the planet's atmosphere and geology suggest that it may have been habitable in the past. NASA's Curiosity rover has been exploring Mars since 2012, and has discovered evidence of water on the planet, which is a key ingredient for life.
    
    Mars is also a popular target for space missions and future human settlements. Several space agencies and private companies are planning missions to Mars in the coming years, with the goal of establishing a human presence on the planet. The challenges of establishing a human settlement on Mars are significant, including the harsh environment, lack of resources, and distance from Earth. However, many experts believe that Mars is the next logical step in the exploration of the solar system and the expansion of human civilization.
    
    Overall, Mars is a fascinating and complex planet that continues to capture the imagination of scientists and the public alike. Its potential for supporting life and serving as a stepping stone for human exploration of the solar system make it an important target for future space missions and settlements.



```python
print(finetuned_model("taylor swift's best friend"))
```

    
    
    Taylor Swift's best friend is a person who has been by her side through thick and thin. Here are some possible candidates:
    
    1. Abigail Anderson - Abigail is Taylor's childhood friend and has been a constant presence in her life. The two have been inseparable since they met in kindergarten and have shared countless memories together.
    2. Selena Gomez - Selena and Taylor have been friends for over a decade and have been through a lot together. They have collaborated on music projects, gone on vacation together, and have been there for each other through personal struggles.
    3. Liz Rose - Liz is a songwriter and producer who has worked with Taylor on many of her hit songs. The two have a close professional relationship and have also become close friends over the years.
    4. Joe Jonas - Joe and Taylor were in a relationship for a few years in the early 2000s and have remained close friends since then. They have been spotted together at various events and have even collaborated on music projects.
    5. Ed Sheeran - Ed and Taylor have been friends for several years and have collaborated on several songs together. They have a close bond and have been there for each other through personal struggles and triumphs.
    
    Overall, Taylor Swift's best friend is someone who has been a constant source of support and encouragement in her life. Whether it's a childhood friend, a music collaborator, or a romantic partner, Taylor's best friend has been there for her through thick and thin.



```python
print(finetuned_model("""Agent: I'm here to help you with your Amazon deliver order.
Customer: I didn't get my item
Agent: I'm sorry to hear that. Which item was it?
Customer: the blanket
Agent:"""))
```

    I see. Can you please provide me with your order number so I can look into this for you?
    Customer: I don't have the order number.
    Agent: Okay, no worries. Can you please tell me the name of the item you didn't receive?
    Customer: It was a blue blanket.
    Agent: I see. I'm going to check on the status of your order for you. Can you please hold for just a moment?
    Customer: Okay, thank you.
    Agent: (pause) I apologize, but it looks like your order was delivered to the wrong address. Can you please provide me with your correct address so I can assist you in getting the blanket delivered to you?
    Customer: (sighs) I don't know why this is happening to me. I've been ordering from Amazon for years and never had any problems.
    Agent: I apologize for any inconvenience this has caused. I'm here to help you resolve the issue as quickly as possible. Can you please provide me with your correct address so I can assist you?
    Customer: (frustrated) Fine. It's 123 Main St, Apartment 302. Can you please fix this and get my blanket delivered to me?
    Agent: (nodding) Of course, I understand. I'm going to go ahead and update the address on your order. Can you please hold for just a moment while I process this?
    Customer: (sighs) Okay, thank you.
    Agent: (pause) Great, I've updated the address on your order. Your blanket should be delivered to you within the next 3-5 business days. Is there anything else I can assist you with?
    Customer: (disappointed) No, that's all. Thank you for your help.
    Agent: You're welcome. Is there anything else I can do for you?
    Customer: (hesitates) No, that's all. Thank you again.
    Agent: You're welcome. Have a great day!
    
    In this scenario, the customer service agent is trying to help the customer resolve an issue with their Amazon delivery order. The customer did not receive the item they ordered, and the agent is working to update the address on the order to ensure that the customer receives their item as soon as possible. The agent is empathetic and professional throughout the conversation, and provides clear and concise explanations of the steps they are taking to resolve the issue.


### Compare to ChatGPT

> Note: This section of the notebook has been updated.

When run with the query:

```Tell me how to train my dog to sit```

ChatGPT responds with:

> Training your dog to sit is a basic and essential command that can be taught using positive reinforcement. Here's a simple step-by-step guide:
> 1. **Prepare Treats:**
   Gather small, soft treats that your dog enjoys. Make sure they are easy to chew and won't take too long to eat.
> 2. **Find a Quiet Space:**
   Choose a quiet area with minimal distractions for the training session. This will help your dog focus better.
> 3. **Get Your Dog's Attention:**
   Call your dog's name to get their attention. Make sure they are looking at you.
> 4. **Use a Treat to Lure:**
   Hold a treat close to your dog's nose, and slowly move your hand upward and slightly backward over their head. As you do this, your dog's natural response will be to follow the treat with their nose, causing them to sit.
> 5. **Say the Command:**
   As your dog starts to sit, say the command "Sit" in a clear and firm voice. Use the word consistently every time you want your dog to sit.
> 6. **Reward and Praise:**
   As soon as your dog sits, immediately reward them with the treat and offer verbal praise. This positive reinforcement will help them associate sitting with positive outcomes.
> 7. **Repeat and Practice:**
   Repeat the process several times in a row during each training session. Keep the sessions short (around 5-10 minutes) to prevent your dog from losing interest.
> 8. **Add Duration:**
   Once your dog consistently sits on command, you can gradually increase the duration by waiting a couple of seconds before giving the treat. This helps reinforce the sit command.
> 9. **Generalize the Command:**
   Practice the "sit" command in different locations and with various distractions to help your dog generalize the behavior.
> 10. **Be Patient and Consistent:**
    Patience and consistency are key in dog training. Always use positive reinforcement, and avoid punishment. If your dog doesn't succeed initially, go back a step and try again.
> 
> Remember that each dog is unique, and some may learn more quickly than others. Adjust your training approach based on your dog's individual needs and progress.


```python

```
