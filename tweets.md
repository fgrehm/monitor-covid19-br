---
layout: page
title: Tweets
hero_height: is-small
permalink: /tweets/
---

{% assign sorted_tweets = site.data.tweets | sort: "published_at" | reverse %}
{% assign last_tweet = sorted_tweets | first %}

**Última atualização {{ last_tweet.published_at | date: "%Y-%m-%d %H:%M %z" }}**

<table data-order='[[ 0, "desc" ]]' data-page-length='25'>
  <thead>
    <tr>
      <th>Tweet</th>
    </tr>
  </thead>
  <tbody>
    {% for tweet in sorted_tweets %}
    <tr>
      <td>
        <strong>
           {{ tweet.published_at | date: '%Y-%m-%d %H:%M' }}
           {{ tweet.source_name }}
        </strong>
        <br>
        "{{ tweet.full_text }}"
        <strong><a href="{{ tweet.link }}">link</a></strong>
      </td>
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
