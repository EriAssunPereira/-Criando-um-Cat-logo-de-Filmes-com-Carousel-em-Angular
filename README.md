# Criando-um-Catálogo-de-Filmes-com-Carousel-em-Angular

Para criar um catálogo de filmes com um carousel em Angular, vamos seguir os passos abaixo, organizando tudo em módulos.

### Passo 1: Estrutura do Projeto

Primeiro, vamos criar a estrutura básica do projeto Angular:

```bash
ng new angular-movie-catalog
cd angular-movie-catalog
```

### Passo 2: Configuração do Bootstrap (opcional)

Se você deseja utilizar o Bootstrap para estilização e o carousel, pode adicioná-lo ao projeto:

```bash
npm install bootstrap
```

Em seguida, adicione o Bootstrap ao arquivo `styles.scss`:

```scss
@import '~bootstrap/dist/css/bootstrap.min.css';
```

### Passo 3: Criando Módulos

#### 3.1. Módulo de Filmes

Vamos criar um módulo para lidar com o catálogo de filmes:

```bash
ng generate module movies
```

Dentro do módulo `movies`, vamos ter os seguintes componentes:

- `movie-list.component.html`: Lista de filmes.
- `movie-carousel.component.html`: Carousel para exibição dos filmes.

Exemplo de `movie-list.component.html`:

```html
<div class="container">
  <div class="row">
    <div class="col">
      <h2>Filmes em Destaque</h2>
      <div class="carousel">
        <ngb-carousel>
          <ng-template ngbSlide *ngFor="let movie of movies">
            <img [src]="movie.posterUrl" class="d-block w-100" alt="{{ movie.title }}">
            <div class="carousel-caption">
              <h3>{{ movie.title }}</h3>
              <p>{{ movie.description }}</p>
            </div>
          </ng-template>
        </ngb-carousel>
      </div>
    </div>
  </div>
</div>
```

#### 3.2. Módulo Principal

Vamos configurar o módulo principal do Angular para incluir o roteamento e importar os módulos necessários:

```typescript
import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
import { NgbModule } from '@ng-bootstrap/ng-bootstrap';

import { AppRoutingModule } from './app-routing.module';
import { AppComponent } from './app.component';
import { MoviesModule } from './movies/movies.module';

@NgModule({
  declarations: [
    AppComponent
  ],
  imports: [
    BrowserModule,
    AppRoutingModule,
    NgbModule,
    MoviesModule
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }
```

### Passo 4: Configurando Dados de Exemplo

Vamos adicionar dados de exemplo para os filmes em `movies.service.ts` dentro do módulo `movies`:

```typescript
import { Injectable } from '@angular/core';

@Injectable({
  providedIn: 'root'
})
export class MoviesService {

  private movies = [
    {
      title: 'Filme 1',
      description: 'Descrição do Filme 1.',
      posterUrl: 'assets/movie1.jpg'
    },
    {
      title: 'Filme 2',
      description: 'Descrição do Filme 2.',
      posterUrl: 'assets/movie2.jpg'
    },
    {
      title: 'Filme 3',
      description: 'Descrição do Filme 3.',
      posterUrl: 'assets/movie3.jpg'
    }
  ];

  constructor() { }

  getMovies() {
    return this.movies;
  }
}
```

### Passo 5: Implementando Componentes

Implemente os componentes e serviços conforme necessário nos respectivos módulos. Certifique-se de adicionar imagens de exemplo (`movie1.jpg`, `movie2.jpg`, `movie3.jpg`) na pasta `src/assets`.

### Passo 6: Estilizando e Personalizando

Personalize o estilo do carousel e dos componentes conforme desejado utilizando CSS ou classes do Bootstrap.

### Passo 7: Testando e Executando

Teste o projeto com o comando:

```bash
ng serve
```

Navegue para `http://localhost:4200/` para ver o catálogo de filmes com o carousel em ação.

Este é um esqueleto básico para criar um catálogo de filmes com carousel em Angular. Poderemos expandir adicionando funcionalidades como detalhes de filmes, filtros de categoria, etc., conforme necessário.
