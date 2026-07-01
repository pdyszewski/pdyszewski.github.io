```{=html}
<div class="pub-list list">
<% for (const item of items) {
  const authors = Array.isArray(item.authors) ? item.authors.join(", ") : item.authors;
  const year = item.year || (item.date ? new Date(item.date).getFullYear() : "");
%>
  <article class="pub-item" <%= metadataAttrs(item) %>>
    <div class="pub-year listing-date"><%- year %></div>

    <div class="pub-main">
      <div class="pub-body">
        <div class="pub-type listing-type"><%- item.type || "" %></div>

        <h3 class="pub-title listing-title">
          <%- item.title || "" %>
        </h3>

        <div class="pub-authors listing-authors">
          <%- authors || "" %>
        </div>

        <div class="pub-venue listing-venue">
          <em><%- item.venue || "" %></em>
        </div>

        <% if (item.description) { %>
          <p class="pub-description"><%- item.description %></p>
        <% } %>

        <div class="pub-links">
          <% if (item.pdf) { %><a href="<%- item.pdf %>">PDF</a><% } %>
          <% if (item.doi) { %><a href="<%- item.doi %>">DOI</a><% } %>
          <% if (item.slides) { %><a href="<%- item.slides %>">Slides</a><% } %>
          <% if (item.cite) { %><a href="<%- item.cite %>">BibTeX</a><% } %>
          <% if (item.arxiv) { %><a href="<%- item.arxiv %>">arXiv</a><% } %>
        </div>

        <% if (item.bibtex) { %>
          <details class="pub-cite">
            <summary>Cite</summary>
            <pre><code><%- item.bibtex %></code></pre>
          </details>
        <% } %>
      </div>

      <% if (item.image) { %>
        <div class="pub-image-wrap">
          <img
            class="pub-image"
            src="<%- item.image %>"
            alt="<%- item.image_alt || item.title || 'Publication image' %>"
            loading="lazy"
          />
        </div>
      <% } %>
    </div>
  </article>
<% } %>
</div>
```