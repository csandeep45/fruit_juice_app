# fruit_juice_app
import streamlit as st

# Sample data dictionary
data = {
    "Juice_type": ['Orange', 'Pine Apple', 'Apple'],
    "Avg_VIT": [2.5, 3.5, 4.5],
    "Avg_MIN": [1.5, 2.5, 3.5]
}

# Streamlit app
def main():
    st.title("Fruit Juice App")
    selected_type = st.selectbox("Select Juice type:", data["Juice_type"])
    selected_measure = st.selectbox("Select Measure:",    list(data.keys())[1:]) # Exclude "Juice_type"
    index = data["Juice_type"].index(selected_type)
    selected_value = data[selected_measure][index]
    st.write(f"The {selected_measure} for {selected_type} is         {selected_value}")
    
    num_juices_per_day = st.selectbox("Select Number of Juices Per Day:", [1, 2, 3, 4])
    
    if selected_measure == "Avg_VIT":
        yearly_grams = 1000 * (selected_value / 100) * 365 * num_juices_per_day
        st.write(f"If you drink {num_juices_per_day} {selected_type} juice(s) per day, you would consume approximately {yearly_grams:.2f} grams of vitamins per year.")
    if selected_measure == "Avg_MIN":
        yearly_grams = 1000 * (selected_value / 100) * 365 * num_juices_per_day
        st.write(f"If you drink {num_juices_per_day} {selected_type} juice(s) per day, you would consume approximately {yearly_grams:.2f} grams of minerals per year.")

if __name__ == "__main__":
    main()

