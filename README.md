# [Responsive Navigation Bar](https://github.com/Lucas-Henrique-Lopes-Costa/Barra-de-Navegacao-Responsivel)

### Demonstration: <a href="https://lucas-henrique-lopes-costa.github.io/Barra-de-Navega-o-Responsivo/" target="_blank">Site Preview</a>
#### USABILITY DEMONSTRATION VIDEO:
<a href="https://youtu.be/ZZExO4Ve5DE"><img align="center" width="100%" src="https://github.com/Lucas-Henrique-Lopes-Costa/Lucas-Henrique-Lopes-Costa/blob/main/Demonstration-Videos/Barra-de-Navega%C3%A7%C3%A3o-Respons%C3%A1vel.gif?raw=true"></img></a>

## Training CSS
<h6>Variáveis CSS:</h6>

Definindo variáveis para o estilo de **fontes e cores**.
Isso porque com o JavaScript iremos mudar o estilo do layout.

<h6>Barra de Rolagem:</h6>


````
body::-webkit-scrollbar { /* :tamanho da barra de rolagem */
  width: 0.25rem;
}

body::-webkit-scrollbar-track { /* :cor de fundo da barra de rolagem */
  background: var(--bg-primary);
}

body::-webkit-scrollbar-thumb { /* :mudando a cor da barra de rolagem de dentro */
  background: #6649b8;
}
````
<h4>Barra de Navegação</h4>

Para rotacionar o **Logo** quando passamos o mouse, usamos:

```
.navbar:hover .logo svg {
  transform: rotate(-180deg);
}
```
porque quando passa o mouse em cima (``.navbar:hover``) ele transforma tudo em *-180 grau*

<h4>Parte Responsivo</h4>

<h5>Telas Pequenas</h5>

````
@media only screen and (max-width: 600px) {
  .navbar {
    bottom: 0;
    width: 100vw;
    height: 5rem;
  }

  .logo {
    display: none;
  }

  .navbar-nav {
    flex-direction: row;
  }

  .nav-link {
    justify-content: center;
  }

  main {
    margin: 0;
  }
}
````

Para definir _onde_ irá ficar a barra de navegação, usamos o ``bottom: 0``,ou seja, **não terá espaço na parte de baixo** do elemento. Logo, ficará colado com a parte de baixo.

Definimos o "logo" como ``display: none;`` para ele não aparecer.

<h5>Telas Grandes</h5>

```
@media only screen and (min-width: 600px) {
  .navbar {
    top: 0;
    width: 5rem;
    height: 100vh;
  }

  .navbar:hover {
    width: 16rem;
  }

  .navbar:hover .link-text {
    display: inline;
  }

  .navbar:hover .logo svg {
    margin-left: 11rem;
  }

  .navbar:hover .logo-text {
    left: 0px;
  }
}
```

Sem a configuração de ``top: 0; width: 5rem; height: 100vh;`` a barrra de naveção não preenche tudo, então usamos o ``height: 100vh``, porque ele mede o tamamnho do elemento levando em conta o _viewport height_.

Já quando passamos o mouse em cima da barra de navegação, ele define o comprimento sendo ``width: 16rem;``, para **expandir** essa barra de navegação.

---

## Training JS
Usando Java Script para mudar o **tipo de tema** do layout. 

Quando clicar no botão que possue o **id: themeButton** chama a função "toggleTheme".

````
function toggleTheme() {
  const current = localStorage.getItem("theme");
  const next = themeMap[current];
  
  console.log("Estava no: " + current);
  console.log("Agora é o: " + next);

  bodyClass.replace(current, next);
  localStorage.setItem("theme", next);
}
````

Na função "toogleTheme" usamos uma função chamada ["localStorage"](https://www.w3schools.com/jsref/prop_win_localstorage.asp) que atribui à variável __current__ o tema ("theme") atual.

Depois para pegar o **próximo tema**, usamos um objeto que é um dicionário: _para cada tema atual, qual deve ser o próximo_. Esse valor é armazenado na variável *next*.

Com esses valores, mudamos o tema atual pelo o próximo usando _**.replace**_ e depois com o **_localStorage.setItem_** mudamos o tema para próximo.
