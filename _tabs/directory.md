---
layout: page
title: 目录
icon: fas fa-folder-open
order: 2
permalink: /directory/
---

<style>
  .directory-page {
    --directory-accent: var(--link-color, #315efb);
    --directory-heading: var(--heading-color, #1f2937);
    --directory-muted: var(--text-muted-color, #6b7280);
    --directory-border: var(--main-border-color, rgba(127, 127, 127, 0.22));
    --directory-card: var(--card-bg, rgba(127, 127, 127, 0.08));
    margin-top: 1.5rem;
  }

  .directory-hero {
    position: relative;
    overflow: hidden;
    margin-bottom: 1.5rem;
    padding: clamp(1.25rem, 3vw, 2rem);
    border: 1px solid var(--directory-border);
    border-radius: 1rem;
    background:
      radial-gradient(circle at 100% 0%, color-mix(in srgb, var(--directory-accent) 16%, transparent), transparent 38%),
      linear-gradient(135deg, var(--directory-card), transparent 70%);
  }

  .directory-hero::after {
    position: absolute;
    right: 1.5rem;
    bottom: -2rem;
    width: 7rem;
    height: 7rem;
    border: 1px solid color-mix(in srgb, var(--directory-accent) 25%, transparent);
    border-radius: 50%;
    content: '';
  }

  .directory-eyebrow {
    margin-bottom: 0.45rem;
    color: var(--directory-accent);
    font-size: 0.75rem;
    font-weight: 700;
    letter-spacing: 0.12em;
    text-transform: uppercase;
  }

  .directory-hero h1 {
    position: relative;
    z-index: 1;
    margin: 0 0 0.6rem;
    color: var(--directory-heading);
  }

  .directory-hero p {
    position: relative;
    z-index: 1;
    max-width: 42rem;
    margin: 0;
    color: var(--directory-muted);
  }

  .directory-stats {
    position: relative;
    z-index: 1;
    display: flex;
    flex-wrap: wrap;
    gap: 0.5rem 1rem;
    margin-top: 1.1rem;
    color: var(--directory-muted);
    font-size: 0.85rem;
  }

  .directory-stats strong {
    color: var(--directory-heading);
    font-size: 1rem;
  }

  .directory-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(min(100%, 19rem), 1fr));
    gap: 1rem;
  }

  .directory-folder {
    align-self: start;
    overflow: hidden;
    border: 1px solid var(--directory-border);
    border-radius: 0.85rem;
    background: var(--directory-card);
    transition: border-color 180ms ease, box-shadow 180ms ease, transform 180ms ease;
  }

  .directory-folder:hover,
  .directory-folder[open] {
    border-color: color-mix(in srgb, var(--directory-accent) 48%, var(--directory-border));
    box-shadow: 0 0.8rem 2rem color-mix(in srgb, var(--directory-accent) 12%, transparent);
  }

  .directory-folder:hover {
    transform: translateY(-2px);
  }

  .directory-folder__summary {
    display: flex;
    align-items: center;
    gap: 0.7rem;
    min-height: 4rem;
    padding: 0.9rem 1rem;
    cursor: pointer;
    list-style: none;
  }

  .directory-folder__summary::-webkit-details-marker {
    display: none;
  }

  .directory-folder__chevron {
    color: var(--directory-muted);
    font-size: 0.85rem;
    transition: transform 180ms ease;
  }

  .directory-folder[open] .directory-folder__chevron {
    transform: rotate(90deg);
  }

  .directory-folder__icon {
    display: grid;
    flex: 0 0 2.25rem;
    place-items: center;
    width: 2.25rem;
    height: 2.25rem;
    border-radius: 0.65rem;
    background: color-mix(in srgb, var(--directory-accent) 13%, transparent);
    color: var(--directory-accent);
  }

  .directory-folder__name {
    min-width: 0;
    flex: 1;
    overflow: hidden;
    color: var(--directory-heading);
    font-weight: 700;
    text-overflow: ellipsis;
    white-space: nowrap;
  }

  .directory-folder__count {
    flex: 0 0 auto;
    color: var(--directory-muted);
    font-size: 0.78rem;
  }

  .directory-folder__body {
    padding: 0.1rem 1rem 1rem 1.25rem;
    border-top: 1px solid var(--directory-border);
  }

  .directory-posts {
    margin: 0.85rem 0 0 0.55rem;
    padding: 0 0 0 1rem;
    border-left: 1px solid var(--directory-border);
    list-style: none;
  }

  .directory-post {
    position: relative;
    display: flex;
    align-items: baseline;
    justify-content: space-between;
    gap: 0.75rem;
    padding: 0.45rem 0;
  }

  .directory-post::before {
    position: absolute;
    top: 1.05rem;
    left: -1rem;
    width: 0.75rem;
    border-top: 1px solid var(--directory-border);
    content: '';
  }

  .directory-post a {
    min-width: 0;
    color: var(--directory-heading);
    font-size: 0.94rem;
    line-height: 1.45;
  }

  .directory-post a:hover {
    color: var(--directory-accent);
  }

  .directory-post time {
    flex: 0 0 auto;
    color: var(--directory-muted);
    font-size: 0.72rem;
    white-space: nowrap;
  }

  @media (max-width: 576px) {
    .directory-post {
      display: block;
    }

    .directory-post time {
      display: block;
      margin-top: 0.2rem;
    }
  }
</style>

<div class="directory-page">
  <section class="directory-hero" aria-labelledby="directory-title">
    <div class="directory-eyebrow">Folder index</div>
    <h1 id="directory-title">按文件夹浏览文章</h1>
    <p>这里按照你在 <code>_posts</code> 中使用的分类组织文章。点击文件夹名称即可展开或收起对应内容。</p>
    <div class="directory-stats" aria-label="目录统计">
      <span><strong>{{ site.categories.size }}</strong> 个文件夹</span>
      <span><strong>{{ site.posts.size }}</strong> 篇文章</span>
    </div>
  </section>

  <section class="directory-grid" aria-label="文章文件夹列表">
    {% assign directory_groups = site.categories | sort %}
    {% for group in directory_groups %}
      {% assign directory_posts = group[1] | sort: "date" | reverse %}
      <details class="directory-folder" open>
        <summary class="directory-folder__summary">
          <span class="directory-folder__chevron" aria-hidden="true">▸</span>
          <span class="directory-folder__icon" aria-hidden="true"><i class="fas fa-folder-open"></i></span>
          <span class="directory-folder__name">{{ group[0] }}</span>
          <span class="directory-folder__count">{{ directory_posts.size }} 篇</span>
        </summary>
        <div class="directory-folder__body">
          <ul class="directory-posts">
            {% for post in directory_posts %}
              <li class="directory-post">
                <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
                <time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%Y/%m/%d" }}</time>
              </li>
            {% endfor %}
          </ul>
        </div>
      </details>
    {% endfor %}
  </section>
</div>
