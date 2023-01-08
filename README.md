# PROGRAMMING FOR DATA SCIENCE - FIT - HCMUS
## Final Project - Thu thập, phân tích cho trả lời câu hỏi về bộ dữ liệu MyAnimeList
### I. Thông tin nhóm:
- Lớp: 20KHDL2

#|Họ tên
-|-
20127383|Lê Ngọc Tường
20127484|Nguyễn Tư Duy

### II. Thông tin đề tài:
#### **_01. Dataset:_**
[MyAnimeList Anime and Manga Datasets](https://www.kaggle.com/datasets/andreuvallhernndez/myanimelist) chứa thông tin của 67.273 bộ truyện.

#### **_02. Meaningful questions:_**
- Những bộ manga nào là phù hợp đối với mỗi đối tượng (`demographics`)?
>> Mục đích: cải thiện hệ thống khuyến nghị (recommendation system) của MAL.
- Đâu là những thời điểm bùng nổ của manga, cũng như các `genres` và `themes` phổ biến nhất ở những thời điểm này, tỉ lệ bao nhiêu trong số đó đã thành công đến thời điểm hiện tại.
>> Mục đích: phân tích này mang ý nghĩa thông kê, phân tích để thấy được quá trình phát triển của của ngành công nghiệp manga, đồng thời cũng giúp so sánh với thời điểm hiện tại một phần giúp các mangaka chọn được thể loại và chủ đề sáng tác.
- Đánh giá sự cống hiến cũng như thành công của một mangaka (`authors`) dựa trên hai yếu tố: số bộ manga (`manga_id`) mà người đó tham gia (Story hoặc Art hoặc cả hai) và sự thành công của những bộ đó (`score`).
>> Mục đích: tìm những mangaka cống hiến nhiều nhất để xếp hạng, trao thưởng, tri ân.
- Những thể loại (`genres`) nào được người đọc yêu thích ở thời gian gần đây hơn so với thời gian trước và ngược lại?
>> Mục đích: biết được xu hướng đọc hiện nay của người dùng MAL để có thể tạo ra những bài blogs, articles liên quan đến những thể loại đó.

#### **_03. Questions analysis:_**
- Câu hỏi 1:
  - Đầu tiên là tìm thể loại (`genres`) phổ biến nhất với từng đối tượng.
  - Sử dụng hồi quy tuyến tính dựa vào 3 đầu vào là `scored_by`, `members`, `favorites` để dự đoán `score`.
  - Đưa ra ngưỡng `score` khuyến nghị kết hợp với thể loại đã tìm được ở trên để recommend những manga mang tính khuyến nghị cao cho từng đối tượng.
- Câu hỏi 2:
  - Đếm số manga bắt đầu mỗi năm dựa vào `real_start_date`, thời điểm bùng nổ là những vùng xung quanh cực đại.
  - Tìm các các `genres` và `themes` xuất hiện nhiều nhất trong những thời điểm này.
  - Tìm các bộ manga thuộc các thời điểm, thể loại, chủ đề và dựa vào ngưỡng `score` (lấy score đã có, nếu chưa được đánh giá ta sẽ dùng score dự đoán có được ở câu hỏi 1) được chọn để đánh giá sự thành công của nó.
- Câu hỏi 3:
  - Tính số manga mà mỗi tác giả đã tham gia.
  - Mỗi mangaka sẽ có hai chỉ số:
    - Chỉ số thứ nhất: tính bằng trung bình cộng của tất cả các `score` của tất cả các bộ manga mà mangaka đó tham gia.
    - Chỉ số thứ hai: là số manga mà tác giả đó tham gia.
  - Chuẩn hóa hai chỉ số về dạng thích hợp.
  - Tính tổng của tích chỉ số với trọng số (mỗi chỉ số sẽ có trọng số tương ứng để thể hiện mức độ ảnh hưởng), output sẽ là mức độ cống hiển, thành công của một mangaka.
  - Sau đó ta sẽ lấy ra những mangaka có output cao nhất.
- Câu hỏi 4:
  - Đưa ra threshold cho số lượng người đánh giá (`scored_by`).
  - Với mỗi thể loại, chia số manga thuộc thể loại đó ra làm 2 phần bằng median của thời gian xuất bản (`real_start_date`), sau đó chỉ lấy những bộ nào có `scored_by` >= threshold.
  - Tính trung bình mỗi phần rồi so sánh, output sẽ là list những manga được yêu thích gần đây hơn và list những manga được yêu thích ở thời gian trước hơn.

#### **_04. More Information:_**
- [Github](https://github.com/lengoctuong/Prj-Manga-Dataset_Programming4DS)
- [Trello](https://trello.com/b/kqDOvCG5/prj-manga-datasetprogramming4ds)

#### **_05. Planning:_**
![Planning](./Planning-Image.png)
