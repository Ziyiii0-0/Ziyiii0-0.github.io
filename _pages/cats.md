---
layout: archive
permalink: /cats/
author_profile: true
---

{% include base_path %}

<div class="cat-profile">
  <div class="cat-profile-right">
    <h2 class="cat-name">Cakecake <span>糕糕</span></h2>
    <div class="cat-chips">
      <span class="cat-chip">Female</span>
      <span class="cat-chip">🐾 Munchkin</span>
      <span class="cat-chip">🎂 Aug 5, 2022</span>
    </div>
    <p class="cat-bio">Likes lickable treats, hates canned food, and occasionally tolerates being held. She supervises all my research, sits on my keyboard at critical moments, and graciously allows me to fund her lifestyle.</p>
  </div>
</div>

<div class="cat-gallery-wrap">
  <div class="cat-gallery" id="catGallery">
    <div class="cat-photo"><img src="{{ base_path }}/images/cakecake/CakeCake.jpg" alt="CakeCake"></div>
    <div class="cat-photo"><img src="{{ base_path }}/images/cakecake/cake_sleeping.jpg" alt="CakeCake sleeping"></div>
    <div class="cat-photo"><img src="{{ base_path }}/images/cakecake/cake_fat.jpg" alt="CakeCake chilling"></div>
    <div class="cat-photo"><img src="{{ base_path }}/images/cakecake/IMG_1328.jpg" alt="CakeCake 1"></div>
    <div class="cat-photo"><img src="{{ base_path }}/images/cakecake/IMG_2265.jpg" alt="CakeCake 2"></div>
    <div class="cat-photo"><img src="{{ base_path }}/images/cakecake/IMG_2317.jpg" alt="CakeCake 3"></div>
  </div>
</div>

<script>
(function() {
  var gallery = document.getElementById('catGallery');
  var photos = Array.from(gallery.children);
  for (var i = photos.length - 1; i > 0; i--) {
    var j = Math.floor(Math.random() * (i + 1));
    var tmp = photos[i];
    photos[i] = photos[j];
    photos[j] = tmp;
  }
  photos.forEach(function(el) { gallery.appendChild(el); });

  var emojis = ['💗','💗','💗','🎉','✨','😈','🐾','💕','⭐️','🌸'];

  function spawnEmoji(x, y) {
    var count = 12 + Math.floor(Math.random() * 6);
    for (var i = 0; i < count; i++) {
      (function(i) {
        setTimeout(function() {
          var ox = (Math.random() - 0.5) * 80;
          var oy = (Math.random() - 0.5) * 80;
          var el = document.createElement('span');
          el.textContent = emojis[Math.floor(Math.random() * emojis.length)];
          el.style.cssText = [
            'position:fixed',
            'left:' + (x + ox) + 'px',
            'top:' + (y + oy) + 'px',
            'font-size:' + (12 + Math.random() * 8) + 'px',
            'pointer-events:none',
            'user-select:none',
            'z-index:9999',
            'transition:none',
          ].join(';');
          document.body.appendChild(el);
          var angle = (Math.random() * 2 * Math.PI);
          var dist = 35 + Math.random() * 45;
          var dx = Math.cos(angle) * dist;
          var dy = Math.sin(angle) * dist - 25;
          var duration = 1200 + Math.random() * 600;
          requestAnimationFrame(function() {
            el.style.transition = 'transform ' + duration + 'ms cubic-bezier(.2,.8,.4,1), opacity ' + duration + 'ms ease';
            el.style.transform = 'translate(' + dx + 'px,' + dy + 'px) scale(1.3)';
            el.style.opacity = '0';
          });
          setTimeout(function() { el.remove(); }, duration + 50);
        }, i * 30);
      })(i);
    }
  }

  document.getElementById('catGallery').addEventListener('click', function(e) {
    var photo = e.target.closest('.cat-photo');
    if (photo) spawnEmoji(e.clientX, e.clientY);
  });
})();
</script>

<style>
.cat-profile {
  display: flex;
  align-items: flex-start;
  gap: 20px;
  margin: 0.5em 0 2em 0;
  max-width: 640px;
}
.cat-profile-right {
  flex: 1;
  padding-top: 4px;
}
.cat-name {
  margin: 0 0 8px 0;
  font-size: 1.3em;
  font-weight: 700;
  color: #222;
  border: none !important;
  padding: 0 !important;
}
.cat-name span {
  font-size: 0.75em;
  font-weight: 400;
  color: #aaa;
  margin-left: 4px;
}
.cat-chips {
  display: flex;
  flex-wrap: wrap;
  gap: 6px;
  margin-bottom: 10px;
}
.cat-chip {
  font-size: 0.78em;
  padding: 3px 10px;
  border-radius: 20px;
  background: #f3f3f3;
  color: #555;
  border: 1px solid #e8e8e8;
}
.cat-bio {
  margin: 0;
  font-size: 0.88em;
  color: #777;
  line-height: 1.7;
}

/* Gallery */
.cat-gallery-wrap {
  max-width: 640px;
  max-height: 680px;
  overflow-y: auto;
  scrollbar-width: thin;
  scrollbar-color: #ddd transparent;
}
.cat-gallery-wrap::-webkit-scrollbar {
  width: 5px;
}
.cat-gallery-wrap::-webkit-scrollbar-thumb {
  background: #ddd;
  border-radius: 4px;
}
.cat-gallery {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 10px;
}
.cat-photo {
  overflow: hidden;
  border-radius: 10px;
  aspect-ratio: 1 / 1;
  background: #f0f0f0;
  cursor: pointer;
}
.cat-photo img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
  transition: transform 0.35s ease, filter 0.35s ease;
}
.cat-photo:hover img {
  transform: scale(1.06);
  filter: brightness(1.05) saturate(1.1);
}
</style>
