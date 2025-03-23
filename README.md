# Resume-Screening-and-ranking
 
 def rank_resumes(job_description,resumes):
    #combine job description with resumes
    documents =[job_description] + resumes
    vectorizer = TfidfVectorizer().fit_transform(documents)
    vectors = vectorizer. toarray()

    #calculate cosine similarity
    job_description_vectors = vectors[0]
    resume_vectors = vector [1:]
    cosine_similarities = cosine_similarity([job_description_vector],resume_vectors).flatter

    return cosine_similarities

    #streamlit app
    st.title("AI Resume screening & Candidate Ranking System")

    # Job description input
    st.header("Job Description")
    job_description = st.text_area("enter the job description")

    #file uploader
    st.header("Upload Resumes")
    uploaded_files = st.file_uploader("upload PDF files", type=["pdf"],accept_multiple_file=Transform)

    if uploaded_files and job_description
     st.header("ranking Resumes")

    resumes = []
    for file in uploaded_files:
        text = extract_text_from_pdf(file)
        resumes.append(text)

    # Rank resumes 
    scores =rank_resumes(job_description, resumes)

    # Display scores
    results = pd.DataFrames({"Resume":[file.name for file in uploaded_files],"score":score})
    results = results,sort_values(by="Score",ascending=False)

    st.write(results)
