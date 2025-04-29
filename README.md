# what-if-generator
A fun random What-If generator."
// File: pages/index.js
import { useState } from "react";
import { Share2 } from "lucide-react";

const topics = [
  "the moon turned into cheese",
  "everyone could teleport",
  "cats became world leaders",
  "gravity was optional",
  "emotions were visible colors",
  "time ran backward on weekends",
  "you had to sing everything you said",
  "dreams became real every morning"
];

const effects = [
  "society would collapse instantly",
  "chaos would become the new normal",
  "memes would be the global currency",
  "science would need rewriting",
  "politics would become performance art",
  "dogs might become more intelligent than humans",
  "everyone would have superpowers",
  "every day would feel like a video game"
];

function generateAIWhatIf() {
  const topic = topics[Math.floor(Math.random() * topics.length)];
  const effect = effects[Math.floor(Math.random() * effects.length)];
  return `What if ${topic}, and ${effect}?`;
}

export default function Home() {
  const [scenario, setScenario] = useState("");

  const generateScenario = () => {
    setScenario(generateAIWhatIf());
  };

  const shareScenario = () => {
    if (navigator.share) {
      navigator.share({
        title: "What If Generator",
        text: scenario,
        url: window.location.href
      });
    } else {
      alert("Sharing not supported on this browser.");
    }
  };

  return (
    <div className="flex flex-col items-center justify-center min-h-screen p-4 bg-gradient-to-br from-indigo-100 to-purple-200">
      <h1 className="text-4xl font-bold mb-6 text-center">What If Generator</h1>
      <div className="w-full max-w-xl mb-4 text-center p-6 bg-white shadow-md rounded-2xl text-xl font-medium">
        {scenario || "Click the button to explore a random 'What If?'"}
      </div>
      <div className="flex gap-4">
        <button onClick={generateScenario} className="text-lg px-6 py-3 rounded-2xl shadow-md bg-purple-600 text-white hover:bg-purple-700">
          Generate What If?
        </button>
        <button onClick={shareScenario} className="text-lg px-6 py-3 rounded-2xl shadow-md border border-gray-400 bg-white flex items-center gap-2">
          <Share2 className="w-5 h-5" /> Share
        </button>
      </div>
    </div>
  );
}

// The rest of the files (package.json, tailwind.config.js, etc.) remain the same.
