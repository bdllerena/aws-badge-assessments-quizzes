## Amazon Textract and .NET Workloads

### Q1. What can Amazon Textract analyze? (select one)

- [ ] Images, video, or recorded speech.
- [ ] Images and video.
- [ ] Recorded speech.
- [x] PDF, TIFF, JPEG, and PNG documents

Amazon Textract is primarily concerned with document analysis and does not process video or voice recordings. It uses machine learning to read and process text from these types of document formats.

### Q2. Which is a benefit of Textract ? (select one)

- [ ] Protection from iamges or video with illegal content.
- [x] Extract key insights with high accuracy from virtually any document.
- [ ] Automate and lower the cost of image recognition and video analysis.
- [ ] Unlimited full-resolution photo storage.

The main advantage of Amazon Textract is to extract text and data from documents such as scanned images and PDF files with high accuracy, allowing users to easily search and analyze the content of their documents.

### Q3. Which of the following are true of the AWS Free Tier for Textract? (select two)

- [x] The number of free pages per month varies for the 5 APIs.
- [ ] You get 1 millon pages free each month.
- [x] The free tier period lasts for 12 months.
- [ ] The free tier period lasts for 3 months.

The AWS Free Tier typically offers a certain number of free pages for Textract API calls per month for the first 12 months after creating an AWS account.

### Q4. Which are use cases for Textract? (choose two)

- [ ] Paraphrase detected text.
- [x] Create an intelligent search index.
- [ ] Fact check documents.
- [x] Accelerate the capture and normalization of data from different sources.

Amazon Textract is designed to extract text and data from documents, which can then be used to create a searchable index, making it easy to find information within large document sets. In addition, it can be used to quickly capture information from various document types and formats, normalizing the data so that it can be used in databases, applications or other tools for further processing or analysis. It does not inherently paraphrase detected text or fact-check documents, although the extracted text could be used as input to other systems designed for those purposes.

### Q5. How does Textract indicate confidence in the accuracy of results? (select one)

- [x] Confidence socre.
- [ ] Star rating.
- [ ] Category.
- [ ] Boolean Confidence flag.

It provides a numerical value (usually between 0 and 100) indicating the level of confidence in the accuracy of the information extracted.

### Q6. Which languages does Textract support? (select one)

- [ ] English only.
- [x] English, Spanish, German, Italian, French, and Portuguese.
- [ ] All commonly spoken languages.
- [ ] English, French, Hindi, Mandarin, and Spanish.

Textract is designed to support multiple languages, but does not support all commonly spoken languages and is not limited to English only.

### Q7. Which Textract feature can detect key-value pairs in document images automatically? (select one)

- [x] Form extraction. 
- [ ] Signature detection.
- [ ] Tuple extraction.
- [ ] Database integration.

This function specifically extracts data from forms by identifying and sorting each entry into key-value pairs.

### Q8.What AWS SDK for .NET class is used to access Textract? (select one)

- [ ] AmazonTextractDetectTextClient.
- [ ] AmazonTextractDocumentAnalysisClient.
- [x] AmazonTextractClient.
- [ ] Each of the 5 APIs has its own client class.

This class is typically provided in the AWS SDK for several programming languages, including .NET, to interact with the Amazon Textract service.

### Q9. How does Textract organize detected text in results? (select one)

- [ ] In a Text property.
- [ ] In a text file.
- [ ] In a linked list of characters and positions.
- [x] In a list of Block objects representing page, lines of text, and words.

Block objects contain information such as the type of text detected, the text itself and the confidence score, as well as positional information.

### Q10. Why are some Textract operations synchronous and others asynchronous? (select one)

- [ ] Each synchronous operation has an async counterpart to support modern programming patterns.
- [ ] Synchronous operations are maintained for backwards compatibility with older software.
- [x] Multipage document operations are asynchronous so your application can complete other tasks while the operation completes.
- [ ] To satisfy different developer preferences.

Asynchronous operations allow larger or more complex tasks to be processed in the background without blocking the main thread of an application, which is important for efficient performance, especially when dealing with multi-page documents that may take longer to process.

### Q11. What are the characteristics of an optimal input document for Textract? (select one)

- [ ] Document does not contain handwriting.
- [x] Document is a high quality image of at least 150 DPI, in a supported format and language.
- [ ] Document does not contain smudges.
- [ ] Document is tagged to give Textract hints about its layout.

Textract works best with high-resolution images because details are sharper, which improves the accuracy of text detection and extraction.

### Q12. In Form Extraction, how is extracted data represented? (select one)

- [ ] As an HTML table.
- [x] As key-value pairs, such as key "Name", value "Jane Doe".
- [ ] As XML elements with name and value attributes.
- [ ] As name-value-position tuples.

This format is used to represent the structure of the forms, where each field (key) is associated with its corresponding content (value).

### Q13. Textract enables human review workflow by integrating with which service? (select one)

- [ ] Amazon Alexa.
- [ ] AWS Lambda.
- [ ] Amazon S3.
- [x] Amazon Augmented AI (A2I).

This service allows you to create the necessary workflows for human review of machine learning predictions, which is useful for validating Textract results and ensuring high-quality data extraction.

### Q14. Which activity is the Analyze Lending API suitable for? (select one)

- [x] Classify and split mortgage loan documents by document type.
- [ ] Assess an applicant's eligibility for a loan.
- [ ] Run a fraudulent activity check on a loan applicant.
- [ ] Optimize loan parameters for maximum profitability.

This API is designed to help streamline the loan application process by using machine learning to automatically classify and extract information from various types of mortgage loan-related documents.

### Q15. How can you estimate your Textract quota needs? (select one)

- [x] Use the Services Quotas Calculator in the AWS console.
- [ ] Use the AWS Pricing Calculator.
- [ ] Track your daily Extract usage for 3 months and find your maximum daily usage.
- [ ] Textract automatically adjusts your quotas based on usage.

The AWS Service Quotas Calculator allows you to estimate your usage and understand the limits applied to your account.

### Q16. Which of these quotas can be changed in the Service quotas console (select two)

- [ ] Character set.
- [x] TPS.
- [ ] ID types.
- [x] Concurrent job limit

These quotas are related to the rate at which you can call the Textract API and the number of jobs you can have running simultaneously, and can often be increased on demand through the AWS Management Console.