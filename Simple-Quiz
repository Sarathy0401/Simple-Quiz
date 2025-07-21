import streamlit as st
import time
import random

# Full question set: mix of general + math
questions = [
    {"question": "What is the capital of France?", "options": ["Berlin", "Paris", "Rome", "Madrid"], "answer": "Paris"},
    {"question": "Which planet is known as the Red Planet?", "options": ["Earth", "Mars", "Jupiter", "Venus"], "answer": "Mars"},
    {"question": "What is 5 + 7?", "options": ["10", "11", "12", "13"], "answer": "12"},
    {"question": "What is 8 - 3?", "options": ["4", "5", "6", "7"], "answer": "5"},
    {"question": "What is 6 × 2?", "options": ["10", "11", "12", "13"], "answer": "12"},
    {"question": "What is 16 ÷ 4?", "options": ["2", "3", "4", "5"], "answer": "4"},
    {"question": "What is 9 + 1?", "options": ["10", "11", "12", "13"], "answer": "10"}
]

# Shuffle and select a few
if 'quiz_set' not in st.session_state:
    st.session_state.quiz_set = random.sample(questions, 5)

# Initialize session state
if 'username' not in st.session_state:
    st.session_state.username = ''
if 'step' not in st.session_state:
    st.session_state.step = 0
if 'score' not in st.session_state:
    st.session_state.score = 0

st.title("📚 General & Math Quiz (Streamlit)")

# Username entry
if st.session_state.username == '':
    st.session_state.username = st.text_input("Enter your name to begin:")
    st.stop()

st.subheader(f"Welcome, {st.session_state.username}! 👋")

# Show current question
if st.session_state.step < len(st.session_state.quiz_set):
    q = st.session_state.quiz_set[st.session_state.step]
    st.write(f"**Q{st.session_state.step + 1}: {q['question']}**")
    selected = st.radio("Choose your answer:", q["options"], key=f"q{st.session_state.step}")

    if st.button("Submit"):
        if selected == q["answer"]:
            st.success("✅ Correct!")
            st.session_state.score += 1
        else:
            st.error(f"❌ Wrong! Correct answer: {q['answer']}")
        st.session_state.step += 1
        time.sleep(1)
        st.rerun()

# Show result after quiz
else:
    st.success(f"🎉 You completed the quiz! Your score: {st.session_state.score}/{len(st.session_state.quiz_set)}")
    if st.button("Restart"):
        for key in list(st.session_state.keys()):
            del st.session_state[key]
        st.rerun()
