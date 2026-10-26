const $ = (id) => document.getElementById(id);
const esc = (s) => String(s ?? '').replace(/[&<>"']/g,
    (c) => ({ '&': '&amp;', '<': '&lt;', '>': '&gt;', '"': '&quot;', "'": '&#39;' }[c]));
const safe = (u) => (/^https?:\/\//i.test(u) ? u : '#');

fetch('profile.json').then((r) => r.json()).then((p) => {
    document.title = `${p.name} | Portfolio`;
    $('name').textContent = p.name;
    if($('name-header')) $('name-header').textContent = `${p.name.toUpperCase()} // SYS.ONLINE`;
    $('tagline').textContent = p.tagline;
    $('bio').textContent = p.bio;

    // Render skills as interactive matrix items
    $('skills').innerHTML = (p.skills || []).map((s) => 
        `<li class="matrix-item">${esc(s)}</li>`).join('');

    // Render projects inside glassmorphic cards
    $('projects').innerHTML = (p.projects || []).map((x, index) =>
        `<div class="glass-card">` +
            `<span class="card-id">SYS_0${index + 1}</span>` +
            `<h3>${esc(x.title)}</h3>` +
            `<p style="color: var(--muted);">${esc(x.desc)}</p>` +
            `<a href="${safe(x.link)}" target="_blank" rel="noopener" style="color: var(--accent); text-decoration: none; font-family: 'JetBrains Mono', monospace; font-size: 0.85rem; display: inline-block; margin-top: 12px;">Explore Repository →</a>` +
        `</div>`).join('');

    // Render navigation social links
    $('links').innerHTML = Object.entries(p.links || {}).map(([k, v]) =>
        `<a href="${safe(v)}" target="_blank" rel="noopener" style="color: var(--accent); font-family: 'JetBrains Mono', monospace; text-decoration: none; font-size: 0.85rem;">[${esc(k)}]</a>`).join('');

    $('footer').innerHTML = `© ${new Date().getFullYear()} ${p.name}. Compiled with focus & code.`;
});
