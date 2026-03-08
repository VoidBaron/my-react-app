import { useState } from "react";

const paradigms = [
  {
    id: "procedural",
    name: "Procedural",
    match: 95,
    tagline: "Your strongest match",
    emoji: "📋",
    color: "#f97316",
    description: "Write code like a recipe — step 1, step 2, step 3. You control every instruction in order.",
    languages: ["Python", "C", "JavaScript", "Go"],
    strengths: ["Clear execution flow", "Easy to trace and debug", "Great for scripting & automation"],
    fits: "You said you think in step-by-step instructions. This is literally that.",
    example: `# Make a sandwich
get_bread()
spread_butter()
add_filling()
serve()`
  },
  {
    id: "oop",
    name: "Object-Oriented",
    match: 88,
    tagline: "Very strong match",
    emoji: "🧱",
    color: "#8b5cf6",
    description: "Model the world as objects — things with properties and behaviors. Like assembling LEGO sets.",
    languages: ["Java", "Python", "C++", "Swift"],
    strengths: ["Models real-world systems", "Organize code into neat categories", "Highly reusable parts"],
    fits: "You enjoy building things and organizing systems — OOP rewards both of these instincts.",
    example: `class Sandwich:
  def __init__(self, filling):
    self.filling = filling
  def serve(self):
    return f"Here's your {self.filling}!"`
  },
  {
    id: "functional",
    name: "Functional",
    match: 72,
    tagline: "Good fit with practice",
    emoji: "🔢",
    color: "#06b6d4",
    description: "Solve problems by composing small, pure functions. Beloved by math and logic lovers.",
    languages: ["Haskell", "Elixir", "Scala", "JavaScript"],
    strengths: ["Elegant transformations", "No hidden side effects", "Great for data pipelines"],
    fits: "Your love of math/logic puzzles and workflows maps here — though it's a different way of thinking at first.",
    example: `# Transform data cleanly
result = list(map(
  lambda x: x * 2,
  filter(lambda x: x > 0, nums)
))`
  },
  {
    id: "declarative",
    name: "Declarative",
    match: 55,
    tagline: "Worth exploring later",
    emoji: "🎯",
    color: "#10b981",
    description: "Describe *what* you want, not *how* to do it. The system figures out the steps.",
    languages: ["SQL", "HTML", "CSS", "Prolog"],
    strengths: ["Very concise", "Great for queries and UI", "Abstracts away complexity"],
    fits: "You prefer explicit control over the steps — this paradigm hides the 'how', which may feel uncomfortable at first.",
    example: `-- Just say what you want
SELECT name, salary
FROM employees
WHERE department = 'Engineering'
ORDER BY salary DESC`
  }
];

export default function ParadigmGuide() {
  const [active, setActive] = useState(paradigms[0]);
  const [showCode, setShowCode] = useState(false);

  return (
    <div style={{
      fontFamily: "'Georgia', 'Times New Roman', serif",
      background: "#0f0f13",
      minHeight: "100vh",
      color: "#e8e4dc",
      padding: "2rem 1.5rem",
      boxSizing: "border-box"
    }}>
      <div style={{ maxWidth: 720, margin: "0 auto" }}>

        {/* Header */}
        <div style={{ textAlign: "center", marginBottom: "2.5rem" }}>
          <div style={{
            fontSize: "0.7rem",
            letterSpacing: "0.3em",
            textTransform: "uppercase",
            color: "#f97316",
            marginBottom: "0.5rem"
          }}>Your Programming Paradigm Profile</div>
          <h1 style={{
            fontSize: "clamp(1.6rem, 4vw, 2.4rem)",
            fontWeight: 400,
            margin: 0,
            lineHeight: 1.2
          }}>You Think Like a <span style={{ color: "#f97316", fontStyle: "italic" }}>Builder</span></h1>
          <p style={{
            color: "#9b9690",
            fontSize: "0.95rem",
            marginTop: "0.75rem",
            maxWidth: 480,
            margin: "0.75rem auto 0"
          }}>Step-by-step logic + assembling systems = Procedural & OOP thinking. Explore your matches below.</p>
        </div>

        {/* Match Cards Row */}
        <div style={{
          display: "grid",
          gridTemplateColumns: "repeat(4, 1fr)",
          gap: "0.6rem",
          marginBottom: "2rem"
        }}>
          {paradigms.map(p => (
            <button
              key={p.id}
              onClick={() => { setActive(p); setShowCode(false); }}
              style={{
                background: active.id === p.id ? "#1a1a22" : "transparent",
                border: `1.5px solid ${active.id === p.id ? p.color : "#2a2a35"}`,
                borderRadius: 10,
                padding: "0.9rem 0.5rem",
                cursor: "pointer",
                color: "#e8e4dc",
                textAlign: "center",
                transition: "all 0.2s",
                boxShadow: active.id === p.id ? `0 0 18px ${p.color}30` : "none"
              }}
            >
              <div style={{ fontSize: "1.4rem" }}>{p.emoji}</div>
              <div style={{
                fontSize: "0.75rem",
                fontWeight: 600,
                marginTop: "0.3rem",
                fontFamily: "monospace"
              }}>{p.name}</div>
              <div style={{
                fontSize: "1rem",
                fontWeight: 700,
                color: p.color,
                marginTop: "0.3rem"
              }}>{p.match}%</div>
            </button>
          ))}
        </div>

        {/* Detail Panel */}
        <div style={{
          background: "#1a1a22",
          border: `1.5px solid ${active.color}40`,
          borderRadius: 14,
          padding: "1.75rem",
          boxShadow: `0 0 40px ${active.color}15`
        }}>
          <div style={{ display: "flex", justifyContent: "space-between", alignItems: "flex-start", flexWrap: "wrap", gap: "0.5rem" }}>
            <div>
              <span style={{
                fontSize: "0.65rem",
                letterSpacing: "0.25em",
                textTransform: "uppercase",
                color: active.color
              }}>{active.tagline}</span>
              <h2 style={{ margin: "0.2rem 0 0", fontSize: "1.5rem", fontWeight: 400 }}>
                {active.emoji} {active.name} Programming
              </h2>
            </div>
            <div style={{
              background: `${active.color}22`,
              border: `1px solid ${active.color}60`,
              borderRadius: 6,
              padding: "0.3rem 0.75rem",
              fontSize: "0.8rem",
              color: active.color,
              fontFamily: "monospace"
            }}>{active.match}% match</div>
          </div>

          <p style={{ color: "#c5c0b8", lineHeight: 1.7, marginTop: "1rem", fontSize: "0.95rem" }}>
            {active.description}
          </p>

          {/* Why it fits you */}
          <div style={{
            background: `${active.color}12`,
            borderLeft: `3px solid ${active.color}`,
            borderRadius: "0 8px 8px 0",
            padding: "0.75rem 1rem",
            marginTop: "1rem",
            fontSize: "0.88rem",
            color: "#e0dbd2",
            fontStyle: "italic"
          }}>
            💡 Why it fits you: {active.fits}
          </div>

          {/* Strengths + Languages */}
          <div style={{ display: "grid", gridTemplateColumns: "1fr 1fr", gap: "1rem", marginTop: "1.25rem" }}>
            <div>
              <div style={{ fontSize: "0.68rem", letterSpacing: "0.2em", textTransform: "uppercase", color: "#6b6760", marginBottom: "0.5rem" }}>Strengths</div>
              {active.strengths.map(s => (
                <div key={s} style={{ fontSize: "0.85rem", color: "#c5c0b8", marginBottom: "0.3rem" }}>
                  <span style={{ color: active.color, marginRight: "0.4rem" }}>▸</span>{s}
                </div>
              ))}
            </div>
            <div>
              <div style={{ fontSize: "0.68rem", letterSpacing: "0.2em", textTransform: "uppercase", color: "#6b6760", marginBottom: "0.5rem" }}>Languages</div>
              <div style={{ display: "flex", flexWrap: "wrap", gap: "0.4rem" }}>
                {active.languages.map(l => (
                  <span key={l} style={{
                    background: "#252530",
                    border: "1px solid #333340",
                    borderRadius: 5,
                    padding: "0.2rem 0.6rem",
                    fontSize: "0.8rem",
                    fontFamily: "monospace",
                    color: "#a09a92"
                  }}>{l}</span>
                ))}
              </div>
            </div>
          </div>

          {/* Code toggle */}
          <button
            onClick={() => setShowCode(s => !s)}
            style={{
              marginTop: "1.25rem",
              background: "transparent",
              border: `1px solid ${active.color}50`,
              borderRadius: 7,
              padding: "0.5rem 1rem",
              color: active.color,
              cursor: "pointer",
              fontSize: "0.82rem",
              fontFamily: "monospace",
              letterSpacing: "0.05em"
            }}
          >
            {showCode ? "▲ Hide example" : "▼ Show code example"}
          </button>

          {showCode && (
            <pre style={{
              background: "#0d0d10",
              border: "1px solid #252530",
              borderRadius: 8,
              padding: "1rem",
              marginTop: "0.75rem",
              fontSize: "0.82rem",
              color: "#a8d8b0",
              fontFamily: "monospace",
              overflowX: "auto",
              lineHeight: 1.6
            }}>{active.example}</pre>
          )}
        </div>

        {/* Footer tip */}
        <p style={{
          textAlign: "center",
          color: "#4a4845",
          fontSize: "0.78rem",
          marginTop: "1.75rem",
          letterSpacing: "0.05em"
        }}>Tap any paradigm card above to explore it · Most real-world code mixes several</p>
      </div>
    </div>
  );
}
