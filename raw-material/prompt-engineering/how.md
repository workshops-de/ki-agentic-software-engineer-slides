---
layout: center
---

# The Prompt Engineering Process

<div class="grid grid-cols-4 gap-4 mt-8">
  <div class="p-4 bg-blue-100 rounded-lg text-center">
    <div class="text-2xl font-bold text-blue-800 mb-2">1</div>
    <h3 class="font-bold text-blue-800">Define Role</h3>
    <p class="text-sm text-blue-700">Who should the AI be?</p>
  </div>
  <div class="p-4 bg-green-100 rounded-lg text-center">
    <div class="text-2xl font-bold text-green-800 mb-2">2</div>
    <h3 class="font-bold text-green-800">Set Context</h3>
    <p class="text-sm text-green-700">What does it need to know?</p>
  </div>
  <div class="p-4 bg-purple-100 rounded-lg text-center">
    <div class="text-2xl font-bold text-purple-800 mb-2">3</div>
    <h3 class="font-bold text-purple-800">Give Instructions</h3>
    <p class="text-sm text-purple-700">What should it do?</p>
  </div>
  <div class="p-4 bg-orange-100 rounded-lg text-center">
    <div class="text-2xl font-bold text-orange-800 mb-2">4</div>
    <h3 class="font-bold text-orange-800">Define Output</h3>
    <p class="text-sm text-orange-700">How should it respond?</p>
  </div>
</div>

---
layout: center
---

# Advanced Prompting Patterns

<div class="grid grid-cols-2 gap-8 mt-8">
  <div class="p-6 bg-blue-50 rounded-lg">
    <h3 class="text-xl font-bold mb-4 text-blue-800">Chain-of-Thought for Debugging</h3>
    <div class="text-sm text-blue-700">
      <p class="mb-2"><strong>Problem:</strong> Component not updating</p>
      <p class="mb-2"><strong>Approach:</strong> "Think step by step about Vue's reactivity system"</p>
      <p><strong>Result:</strong> AI explains the issue and provides solution</p>
    </div>
  </div>
  <div class="p-6 bg-green-50 rounded-lg">
    <h3 class="text-xl font-bold mb-4 text-green-800">Few-Shot for Refactoring</h3>
    <div class="text-sm text-green-700">
      <p class="mb-2"><strong>Problem:</strong> Convert Options API to Composition API</p>
      <p class="mb-2"><strong>Approach:</strong> Show 2-3 examples of conversions</p>
      <p><strong>Result:</strong> AI follows the exact pattern</p>
    </div>
  </div>
</div>

---
layout: center
---

# Best Practices Summary

<div class="grid grid-cols-2 gap-8 mt-8">
  <div class="p-6 bg-green-50 rounded-lg">
    <h3 class="text-xl font-bold mb-4 text-green-800">Do This</h3>
    <ul class="text-left space-y-2 text-green-700">
      <li>✅ Be specific and detailed</li>
      <li>✅ Provide context and examples</li>
      <li>✅ Use structured output formats</li>
      <li>✅ Iterate and refine</li>
      <li>✅ Test with real tools</li>
    </ul>
  </div>
  <div class="p-6 bg-red-50 rounded-lg">
    <h3 class="text-xl font-bold mb-4 text-red-800">Avoid This</h3>
    <ul class="text-left space-y-2 text-red-700">
      <li>❌ Vague, single-sentence prompts</li>
      <li>❌ No context or background</li>
      <li>❌ Unstructured, free-form output</li>
      <li>❌ One-shot, no refinement</li>
      <li>❌ Relying only on AI knowledge</li>
    </ul>
  </div>
</div>

---
layout: center
---

# Quick Reference Card

<div class="grid grid-cols-3 gap-4 mt-8 text-sm">
  <div class="p-4 bg-purple-100 rounded-lg">
    <div class="font-bold text-purple-800 mb-2">🎭 Role</div>
    <p class="text-purple-700">"You are a [expert type]"</p>
  </div>
  <div class="p-4 bg-blue-100 rounded-lg">
    <div class="font-bold text-blue-800 mb-2">🧩 Instructions</div>
    <p class="text-blue-700">"Create [specific thing]"</p>
  </div>
  <div class="p-4 bg-green-100 rounded-lg">
    <div class="font-bold text-green-800 mb-2">🧠 Chain-of-Thought</div>
    <p class="text-green-700">"Think step by step"</p>
  </div>
  <div class="p-4 bg-yellow-100 rounded-lg">
    <div class="font-bold text-yellow-800 mb-2">🧪 Examples</div>
    <p class="text-yellow-700">"Here are examples..."</p>
  </div>
  <div class="p-4 bg-red-100 rounded-lg">
    <div class="font-bold text-red-800 mb-2">🔁 Iterate</div>
    <p class="text-red-700">"Now add [feature]"</p>
  </div>
  <div class="p-4 bg-indigo-100 rounded-lg">
    <div class="font-bold text-indigo-800 mb-2">📑 Format</div>
    <p class="text-indigo-700">"Return as JSON"</p>
  </div>
</div>

<div class="mt-8 p-6 bg-gray-100 rounded-lg">
  <p class="text-lg font-semibold text-center">
    Start with these patterns, then customize for your specific needs
  </p>
</div>
