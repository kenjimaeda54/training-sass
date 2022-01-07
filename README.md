# training-sass
Treinamento Sass

# Motivação
Compreender melhor pre processador Sass e suas ferramentas


## Feature
- Content é um recurso bom para trabalhar conteúdos dinâmicos, algo útil e responsividade.
- Exemplo abaixo mostra o poder de usar content, com ele não precisa passar os parâmetros manualmente ao escopo da do média query.

``` scss

@mixin responsive($type) {
  @if $type == mobile {
    @media screen and (max-width: 320px) {
      // content vai retornar tudo que esta dentro do media
      @content;
    }
  } @else if $type == tablet {
    @media screen and (min-width: 768px) and (max-width: 991px) {
      @content;
    }
  } @else if $type == desktop {
    @media screen and (min-width: 992px) and (max-width: 1199px) {
      @content;
    }
  }
}

nav {
  display: flex;
  height: 1200px;
  padding: 20px;
  width: 100%;
  @include responsive(mobile) {
    //tudo que for colocado isso vai refletir no componente todo
    height: 200vh;
    padding: 10px;
  }
  
}

```

##

- For no Sass segue mesmo principio que outra linguagem, particularidades estão nas escritas.
- Nos determinamos quando inicia e termina, pode usar a palavra reservada to ou through.

``` scss


@for $item from 1 to 6 {
  //comparando par
  @if $item % 2 == 0 {
    .nav-#{$item}:nth-child(#{$item}) {
      color: blue;
      padding: 20px;
      height: 20px;
    }
  }
  @if $item % 2 == 1 {
    .nav-#{$item}:nth-child(#{$item}) {
      color: red;
      padding: 20px;
      height: 20px;
    }
  }
}





```

##

- Outro loop interessante e o each, segue o princípio desestruturação.
- Abaixo tem exemplos trabalhando com ate 3 variáveis.


``` scss

$socialMedias: youtube, linkedin, facebook, twitter, instagram;

@each $network in $socialMedias {
  //vamos criar nossas classes e tambem
  //concatena para pegar as imagens
  .net-#{$network} {
    background-image: url(../images/#{$network}.svg);
  }
}

$socialMedias2: (
  youtube: red,
  linkedin: #6a5acd,
  facebook: rgb(59, 89, 152),
  twitter: #1da1f2,
  instagram: #e1306c,
);
//pode ser qualquer palavra e tipo desestruturação, importante e apos o in
@each $key, $value in $socialMedias2 {
  .work-#{$key} {
    background-color: $value;
  }
}

$socialMedias3: 
  youtube red 21px, 
  linkedin #6a5acd 65px,
  facebook rgb(59, 89, 152) 21px, 
  twitter #1da1f2 19px, 
  instagram #e1306c 21px;

//pode ser qualquer palavra e tipo desestruturação importante e apos in
@each $key, $value, $height in $socialMedias3 {
  .work2-#{$key} {
    background-color: $value;
    height: $height;
    width: $height;
  }
}


```

- Mixin são parecidos com funções. Elas   podem ser reaproveitadas ao longo do sofwtare.
- Abaixo criei um Mixin que foi aproveitado para dois cards.
- Mixin precisam estar incluídas dentro de uma classe para funcionar.
- Funções e Mixin são bens parecidos as diferenças são sucintas, em funções retornamos valores e Mixins são usadas para includes de blocos.

``` scss

@mixin card($backgroundColor, $gap, $status) {
  background-color: $backgroundColor;
  display: flex;
  gap: $gap;
  flex-direction: column;
  justify-content: space-between;
  padding: 20px 20px;
  width: 350px;
  border-radius: 10px;
  position: relative;
  &::before {
    content: "status:" + $status;
    top: 10px;
    right: 10px;
    border-radius: 4px;
    position: absolute;
    background-color: $black;
    color: $white;
    font-size: 12px;
    padding: 12px 5px;
  }

  &:hover {
    background-color: changeColor(light, $backgroundColor);
    cursor: pointer;
  }
}


```

##

- Usei outros recursos do Sass como import, export, variaveis.







