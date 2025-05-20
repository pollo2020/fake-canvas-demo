# fake-canvas-demoimport React, { useState } from "react";

const courses = [
  { name: "Psychology 101", grade: "B", description: "Introduction to human behavior and mental processes." },
  { name: "Statistics 202", grade: "B+", description: "Data analysis, probability, and inferential statistics." },
  { name: "Literature 150", grade: "A-", description: "Exploring classical and modern literary texts." },
  { name: "Theory of Religion", grade: "C", description: "Study of religious beliefs, symbols, and institutions." },
];

export default function FakeCanvas() {
  const [selectedCourse, setSelectedCourse] = useState(null);

  return (
    <div style={{ fontFamily: "Arial, sans-serif", maxWidth: 600, margin: "auto", padding: 20 }}>
      <h1>Fake Canvas Dashboard</h1>
      <ul style={{ listStyle: "none", padding: 0 }}>
        {courses.map((course) => (
          <li
            key={course.name}
            onClick={() => setSelectedCourse(course)}
            style={{
              cursor: "pointer",
              border: "1px solid #ccc",
              marginBottom: 10,
              padding: 10,
              borderRadius: 5,
              backgroundColor: selectedCourse?.name === course.name ? "#e0f7fa" : "white",
            }}
          >
            <strong>{course.name}</strong> — Grade: {course.grade}
          </li>
        ))}
      </ul>

      {selectedCourse && (
        <div style={{ marginTop: 20, padding: 15, border: "1px solid #aaa", borderRadius: 5, backgroundColor: "#fafafa" }}>
          <h2>{selectedCourse.name}</h2>
          <p><strong>Grade:</strong> {selectedCourse.grade}</p>
          <p>{selectedCourse.description}</p>
          <button onClick={() => setSelectedCourse(null)}>Close</button>
        </div>
      )}
    </div>
  );
}
