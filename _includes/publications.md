<div class="publications-heading">
  <h2 id="publications">Publications</h2>
  <button
    type="button"
    class="show-publications-button"
    aria-expanded="false"
    aria-controls="publications-list"
    data-show-text="Show all"
    data-hide-text="Show selected">
    Show all
  </button>
</div>

<div class="publications" id="publications-list">
  <ol class="bibliography">
    {% for link in site.data.publications.main %}
      {% if link.primary_author == true %}
        {% include publication_item.html link=link %}
      {% else %}
        {% include publication_item.html link=link extra_class="secondary-publication" %}
      {% endif %}
    {% endfor %}
  </ol>
</div>

<style>
  /* 默认 Show selected：隐藏非第一作者论文 */
  .publications:not(.show-all-publications) .secondary-publication {
    display: none;
  }
</style>

<script>
  (function () {
    var button = document.querySelector('.show-publications-button');
    var publications = document.querySelector('#publications-list');

    if (!button || !publications) {
      return;
    }

    button.addEventListener('click', function () {
      var expanded =
        publications.classList.toggle('show-all-publications');

      button.setAttribute('aria-expanded', String(expanded));
      button.textContent = expanded
        ? button.dataset.hideText
        : button.dataset.showText;
    });
  })();
</script>
