---
title: pageAction.setPopup()
slug: Mozilla/Add-ons/WebExtensions/API/pageAction/setPopup
tags:
  - API
  - Add-ons
  - Extensions
  - Method
  - Non-standard
  - Reference
  - WebExtensions
  - pageAction
  - setPopup
translation_of: Mozilla/Add-ons/WebExtensions/API/pageAction/setPopup
---
<div>{{AddonSidebar()}}</div>

<p>Définit le document HTML à ouvrir en tant que fenêtre contextuelle lorsque l'utilisateur clique sur l'icône de l'action de la page.</p>

<h2 id="Syntaxe">Syntaxe</h2>

<pre class="brush: js">browser.pageAction.setPopup(
  details // object
)
</pre>

<h3 id="Paramètres">Paramètres</h3>

<dl>
 <dt><code>details</code></dt>
 <dd><p><code>object</code>.</p>
 <dl>
  <dt><code>tabId</code></dt>
  <dd><code>integer</code>. L'ID de l'onglet pour lequel vous souhaitez définir la fenêtre contextuelle.</dd>
  <dt><code>popup</code></dt>
  <dd><code>string</code>. URL vers le fichier HTML à afficher dans un popup. Si elle est définie sur une chaîne vide (''), aucune fenêtre contextuelle n'est affichée.</dd>
 </dl>
 </dd>
</dl>

<h2 id="Compatibilité_du_navigateur">Compatibilité du navigateur</h2>

<p>{{Compat("webextensions.api.pageAction.setPopup")}}</p>

<h2 id="Exemples">Exemples</h2>

<p>Ecoutez les événements {{WebExtAPIRef("tabs.onUpdated")}} et basculez le popup si le statut de chargement change :</p>

<pre class="brush: js">browser.tabs.onUpdated.addListener((tabId, changeInfo, tabInfo) =&gt; {
  if (changeInfo.status) {
    browser.pageAction.show(tabId);
    if (changeInfo.status == "loading") {
      browser.pageAction.setPopup({
        tabId,
        popup: "/popup/loading.html"
      });
    } else {
      browser.pageAction.setPopup({
        tabId,
        popup: "/popup/complete.html"
      });
    }
  }
});</pre>

<p>{{WebExtExamples}}</p>

<div class="note"><p><strong>Note :</strong></p>

<p>Cette API est basée sur l'API Chromium <a href="https://developer.chrome.com/extensions/pageAction"><code>chrome.pageAction</code></a>. Cette documentation est dérivée de <a href="https://chromium.googlesource.com/chromium/src/+/master/chrome/common/extensions/api/page_action.json"><code>page_action.json</code></a> dans le code de Chromium code.</p>

<p>Les données de compatibilité relatives à Microsoft Edge sont fournies par Microsoft Corporation et incluses ici sous la licence Creative Commons Attribution 3.0 pour les États-Unis.</p>
</div>

<div class="hidden">
<pre>// Copyright 2015 The Chromium Authors. All rights reserved.
//
// Redistribution and use in source and binary forms, with or without
// modification, are permitted provided that the following conditions are
// met:
//
//    * Redistributions of source code must retain the above copyright
// notice, this list of conditions and the following disclaimer.
//    * Redistributions in binary form must reproduce the above
// copyright notice, this list of conditions and the following disclaimer
// in the documentation and/or other materials provided with the
// distribution.
//    * Neither the name of Google Inc. nor the names of its
// contributors may be used to endorse or promote products derived from
// this software without specific prior written permission.
//
// THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS
// "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT
// LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR
// A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT
// OWNER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL,
// SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT
// LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE,
// DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY
// THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
// (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
// OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
</pre>
</div>