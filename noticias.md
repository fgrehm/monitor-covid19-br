---
layout: page
title: Notícias
hero_height: is-small
permalink: /noticias/
---

{% assign sorted_articles = site.data.news | sort: "published_at" | reverse %}
{% assign last_article = sorted_articles | first %}

**Última atualização {{ last_article.published_at | date: "%Y-%m-%d %H:%M %z" }}**

<table data-order='[[ 1, "desc" ]]' data-page-length='25'>
  <thead>
    <tr>
      <th>Fonte</th>
      <th>Notícia</th>
    </tr>
  </thead>
  <tbody>
    {% for article in sorted_articles %}
    <tr>
      <td>
        {{ article.state }}<br>
        <a href="{{ article.source_url }}">{{ article.source_name }}</a>
      </td>
      <td>{{ article.published_at | date: '%Y-%m-%d %H:%M' }}<br><a href="{{ article.link }}">{{ article.title }}</a></td>
    </tr>
    {% endfor %}
  </tbody>
</table>

<script src="{{ site.baseurl }}/assets/js/datatables.min.js" type="text/javascript"></script>
<script>
  $(document).ready(
    function () {
      $('table').DataTable({
        language: {
          "sEmptyTable": "Nenhum registro encontrado",
          "sInfo": "Mostrando de _START_ até _END_ de _TOTAL_ registros",
          "sInfoEmpty": "Mostrando 0 até 0 de 0 registros",
          "sInfoFiltered": "(Filtrados de _MAX_ registros)",
          "sInfoPostFix": "",
          "sInfoThousands": ".",
          "sLengthMenu": "_MENU_ resultados por página",
          "sLoadingRecords": "Carregando...",
          "sProcessing": "Processando...",
          "sZeroRecords": "Nenhum registro encontrado",
          "sSearch": "Pesquisar",
          "oPaginate": {
            "sNext": "Próximo",
            "sPrevious": "Anterior",
            "sFirst": "Primeiro",
            "sLast": "Último"
          },
          "oAria": {
            "sSortAscending": ": Ordenar colunas de forma ascendente",
            "sSortDescending": ": Ordenar colunas de forma descendente"
          },
          "select": {
            "rows": {
              "_": "Selecionado %d linhas",
              "0": "Nenhuma linha selecionada",
              "1": "Selecionado 1 linha"
            }
          }
        }
      });
    }
  );
</script>
