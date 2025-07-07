import streamlit as st
import pandas as pd


if "blocks" not in st.session_state:
    st.session_state.blocks = []

st.title("🌿 Tobacco Block Price Calculator")

st.markdown("Each block has its **own weight** and **price per kg**. Total price = weight × price per kg.")


with st.form("block_form"):
    weight = st.number_input("Enter Block Weight (kg)", min_value=0.01, step=0.1, format="%.2f")
    price_per_kg = st.number_input("Enter Price per 1kg (₹)", min_value=0.0, step=1.0, format="%.2f")
    submit = st.form_submit_button("Add Block")

    if submit:
        total_price = weight * price_per_kg
        st.session_state.blocks.append({
            "Block #": len(st.session_state.blocks) + 1,
            "Weight (kg)": weight,
            "Price per kg (₹)": price_per_kg,
            "Block Total (₹)": total_price
        })
        st.success(f"✅ Block added! Block Total: ₹ {total_price:.2f}")


if st.session_state.blocks:
    df = pd.DataFrame(st.session_state.blocks)
    st.subheader("📦 Entered Blocks")
    st.table(df)

    total_blocks = len(df)
    grand_total = df["Block Total (₹)"].sum()

    st.markdown(f"### 🧾 Summary")
    st.markdown(f"- **Total Blocks:** {total_blocks}")
    st.markdown(f"- **Grand Total Amount:** ₹ {grand_total:,.2f}")

    # Clear button
    if st.button("🗑️ Clear All"):
        st.session_state.blocks = []
        st.success("✅ All blocks cleared.")
else:
    st.info("No blocks added yet. Use the form above.")
