<template>

  <section class="src-components-hello-world">
    <div class="code-wrapper">
      <h1 id="title">{{currentHello.lang}}</h1>
      <pre>
      <span id="code">{{currentHello.code}}</span>
      </pre>
    </div>
  </section>

</template>

<script lang="js">

  export default  {
    name: 'src-components-hello-world',
    props: [],
    mounted () {
      this.scrollHellos();
      this.currentHello = this.hellos[0];
    },
    data () {
      return {
        hellos: [
          // ! Java
          {
            lang: 'java',
            code: `
class HelloWorld {
  public static void main(String[] args) {
    System.out.println("Hello, World!"); 
  }
}`
          },
          // ! Golang
          {
            lang: 'Golang',
            code: `
package main

import "fmt"

func main() {
  fmt.Println("hello world")
}`
          },
          // ! C#
          {
            lang: 'C#',
            code: `
using System;
class Program
{
    public static void Main(string[] args)
    {
        Console.WriteLine("Hello, world!");
    }
}`
          },
          // ! Bash
          {
            lang: 'Bash',
            code: `
echo "Hello World"`
          },
          // ! C
          {
            lang: 'C',
            code: `
#include

int main(void)
{
    puts("Hello, world!");
}`
          },
          // ! C++
          {
            lang: 'C++',
            code: `
#include

int main()
{
    std::cout << "Hello, world!";
    return 0;
}`
          },
          // ! JavaScript
          {
            lang: 'JavaScript',
            code: `
document.write('Hello, world!');`
          },
          // ! Obective C
          {
            lang: 'Objective C',
            code: `
#import 
#import

int main(void)
{
    NSLog(@"Hello, world!");
    return 0;
}`
          },
          // ! jQuery
          {
            lang: 'jQuery',
            code: `
$("body").append("Hello world!");`
          },
          // ! Pascal
          {
            lang: 'Pascal',
            code: `
program HelloWorld;
begin
  WriteLn('Hello, world!');
end.`
          },
          // ! Python
          {
            lang: 'Python',
            code: `
print "Hello, world!"`
          },
          // ! Delphi
          {
            lang: 'Delphi',
            code: `
program HelloWorld;

begin
  Writeln('Hello, world!');
end.`
          },
          // ! R
          {
            lang: 'R',
            code: `
cat('Hello, world!')`
          },
          // ! Ruby
          {
            lang: 'Ruby',
            code: `
puts "Hello, world!"`
          },
          // ! Matlab
          {
            lang: 'Matlab',
            code: `
disp('Hello, world!')`
          },
          // ! Logo
          {
            lang: 'Logo',
            code: `
print [Hello, world!]`
          }
        ],
        counter: 0,
        currentHello: '',
        timeToSetNewHello: 7000
      }
    },
    methods: {
      scrollHellos() {
        this.addAnimation();
        setInterval(() => {
          this.counter++;
          this.currentHello = this.hellos[this.counter];
          document.getElementById('code').classList.add('animation-in');
          document.getElementById('title').classList.add('animation-in');
          setTimeout(() => {
            document.getElementById('code').classList.remove('animation-in');
            document.getElementById('title').classList.remove('animation-in');
          }, 1000);
          if(this.counter === this.hellos.length) this.counter = 0;
          this.addAnimation();
          document.getElementById('code').classList.remove('animation');
          document.getElementById('title').classList.remove('animation');
        }, this.timeToSetNewHello);
      },
      addAnimation() {
          setTimeout(() => {
            document.getElementById('code').classList.add('animation');
            document.getElementById('title').classList.add('animation');
          }, 6000);
        }
    },
    computed: {

    }
}


</script>

<style scoped lang="css">

  .src-components-hello-world {
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 60px;
  }

  #title {
    margin-bottom: 20px;
  }

  .code-wrapper {
    max-width: 800px;
    width: 100%;
  }

  .code-wrapper pre {
    background-color: #00000011;
    border-radius: 6px;
    padding: 80px;
    font-size: 20px;
    display: flex;
    align-items: center;
    width: 100%;
    min-height: 400px;
    margin: 0 auto;
    transition: all 1s ease-in-out;
  }

  .animation {
    animation: setNewHello 1s forwards;
  }

  .animation-in {
    animation: animationIn 1s forwards;
  }

  @media (max-width: 800px) {
    .code-wrapper pre {
      padding: 20px;
      font-size: 18px;
    }
  }

  @media (max-width: 700px) {
    .code-wrapper pre {
      padding: 20px;
      font-size: 16px;
      min-height: 300px;
    }

    .src-components-hello-world {
      padding: 40px;
    }
  }

  @media (max-width: 540px) {
    .code-wrapper pre {
      font-size: 12px;
      min-height: 200px;
    }

    .src-components-hello-world {
      padding: 20px;
    }
  }

@media (max-width: 350px) {
  .code-wrapper pre {
    font-size: 10px;
  }
}

@media (max-width: 300px) {
  .code-wrapper pre {
    font-size: 8px;
  }
}

  /* Animations */
  @keyframes animationIn {
    0% {
      opacity: 0;
    }
    100% {
      opacity: 1;
    }
  }

  @keyframes setNewHello {
    20% {
      opacity: 1;
    }
    100% {
      opacity: 0;
    }
  }
</style>
