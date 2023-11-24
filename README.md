<h1 align="center">
  <a href="https://git.io/typing-svg">
    <img src="https://readme-typing-svg.herokuapp.com/?lines=RESTFUL APP;Trabalho Prático&center=true&size=35">
  </a>
</h1>

<p align="center" style="font-size: 30px"><strong>Rafael Eustaquio Pinto | Raphael Henrique | Bernardo Alvim</strong></p>

# <img src="https://hub.meltano.com/assets/static/tmdb.1339262.ba8654571060cac8ca984f640440c1ed.png" height="25">  <b>The Movie Database</b>

O TMDB, ou The Movie Database, é uma plataforma online que fornece informações abrangentes sobre filmes, programas de TV e celebridades. Os desenvolvedores podem acessar dados do TMDB por meio de sua API para criar aplicativos, sites e serviços relacionados a filmes.

## O que é o TMDB?

O TMDB é uma base de dados expansiva que contém informações detalhadas sobre:

- Filmes
- Programas de TV
- Celebridades
- Equipe de produção
- Avaliações e classificações

## Como Acessar o TMDB?

1. **Crie uma conta:** Primeiro, crie uma conta no [site oficial do TMDB](https://www.themoviedb.org).
2. **Solicite uma Chave de API:** Após criar sua conta, acesse o [portal de desenvolvedores do TMDB](https://www.themoviedb.org/settings/api) e solicite uma chave de API.

## Exemplos de códigos aplicados neste projeto

```md
<body>
    <div id="navbarLoader"></div>
    <div id="searchBarLoader"></div>
    <div id="infoLoader"></div>
    <div id="movieListLoader"></div>
    <div id="paginationContainer"></div>
    <div id="modalLoader"></div>


    <script>
        $(document).ready(function () {
            var apiKey = localStorage.getItem('apiKey');

            console.log(apiKey)

            if (!apiKey) {
                $('body').load('components/form.html', configureApiKeyForm)
            } else {
                $('#navbarLoader').load('components/navbar.html', configureNavbar)

                $('#searchBarLoader').load('components/search-bar.html', configureSearchBar)

                loadPopularMoviesList();
            }
        })
    </script>

    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/js/bootstrap.min.js"
        integrity="sha384-BBtl+eGJRgqQAUMxJ7pMwbEyER4l1g+O15P+16Ep7Q9Q+zqX6gSbd85u4mG4QzX+"
        crossorigin="anonymous"></script>

</body>
```
Este bloco faz parte de um arquivo HTML que carrega diferentes componentes, dependendo se há ou não uma chave de API armazenada no localStorage. Se não houver uma chave, um formulário para configurar a chave é carregado; caso contrário, outros componentes são carregados, incluindo uma barra de navegação e uma lista de filmes populares.

```js
function getPopularMovies(page, success, error) {
    $.ajax({
        url: 'https://api.themoviedb.org/3/movie/popular',
        method: 'GET',
        headers: {
            'accept': 'application/json',
            'Authorization': 'Bearer ' + localStorage.getItem('apiKey')
        },
        data: {
            'page': page,
            'language': 'en-US',
            'include_adult': false
        },
        success: success,
        error: error
    });
}
```
```js
function searchMovie(page, success, error, query) {
    $.ajax({
        url: 'https://api.themoviedb.org/3/search/movie',
        method: 'GET',
        headers: {
            'accept': 'application/json',
            'Authorization': 'Bearer ' + localStorage.getItem('apiKey')
        },
        data: {
            'query': query,
            'page': page,
            'language': 'en-US',
            'include_adult': false
        },
        success: success,
        error: error
    });
}
```
```js
function getMovieDetails(movieId, success, error) {
    $.ajax({
        url: 'https://api.themoviedb.org/3/movie/' + String(movieId).trim(),
        method: 'GET',
        headers: {
            'accept': 'application/json',
            'Authorization': 'Bearer ' + localStorage.getItem('apiKey')
        },
        data: {
            'language': 'en-US'
        },
        success: (a) => {
            console.log(a)
            success(a)
        },
        error: error
    });
}
```
As três funções acima utilizam AJAX para fazer requisições à API para obter informações acerca de filmes

##

[🔝 Voltar ao Topo](#)
