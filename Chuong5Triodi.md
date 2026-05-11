# CHƯƠNG 5: QUANG KHẮC

## 5.1 Giới thiệu

Quang khắc là nền tảng cốt lõi của công nghệ chế tạo `IC` hiện đại. Khả năng in các mẫu có chi tiết dưới micron và đặt các mẫu đó lên đế silicon với độ chính xác tốt hơn `0,1 µm` chính là điều làm cho các chip ngày nay trở nên khả thi. Hầu như tất cả các `IC` hiện nay đều được chế tạo bằng quang khắc quang học, là quy trình cơ bản đã được giới thiệu trong Hình `1.9` ở Chương `1`. Khái niệm là đơn giản. Một lớp `photoresist` nhạy sáng được phủ quay lên wafer, tạo thành một lớp mỏng trên bề mặt. Sau đó, lớp `resist` được phơi chọn lọc bằng cách chiếu ánh sáng xuyên qua một `mask` chứa thông tin mẫu cho lớp cụ thể đang được chế tạo. Tiếp theo, `resist` được hiện hình (`develop`), hoàn tất việc chuyển mẫu từ `mask` sang wafer. Như chúng ta đã thấy trong `process flow` ở Chương `2`, `resist` khi đó có thể được dùng làm `mask` để khắc các màng bên dưới, hoặc được dùng làm `mask` cho một bước pha tạp bằng cấy ion.

Mặc dù khái niệm là đơn giản, việc triển khai thực tế lại rất tốn kém và rất phức tạp, chủ yếu do các yêu cầu đặt lên quá trình này về độ phân giải, trường phơi chiếu, độ chính xác đặt vị trí, thông lượng và mật độ khuyết tật. Các yêu cầu về độ phân giải xuất phát từ nhu cầu không ngừng tăng đối với các cấu trúc linh kiện nhỏ hơn. Các yêu cầu về trường phơi chiếu xuất phát từ kích thước chip ngày càng tăng và nhu cầu phải phơi ít nhất một chip hoàn chỉnh (tốt hơn nữa là nhiều hơn) trong mỗi lần phơi. Độ chính xác đặt vị trí là một vấn đề vì nói chung mỗi lớp `mask` cần được căn chỉnh cẩn thận so với các mẫu đã tồn tại sẵn trên wafer. Thông lượng và mật độ khuyết tật dĩ nhiên cũng là các vấn đề do tính cạnh tranh của ngành công nghiệp bán dẫn. Thông lượng chuyển hóa trực tiếp thành chi phí chế tạo. Khuyết tật chuyển hóa trực tiếp thành tổn thất `yield` và do đó làm tăng chi phí của các chip thành phẩm. Các khuyết tật được đưa vào trong quá trình quang khắc là một nguồn đóng góp đáng kể vào `yield` cuối cùng của chip.

`SIA NTRS` xác định các nhu cầu cho các thế hệ công nghệ silicon trong tương lai. Một phần của lộ trình này liên quan đến quang khắc được trình bày trong **Bảng 5.1** `[5.1]`. Có thể rút ra một số nhận xét đáng chú ý từ bảng này. Thứ nhất, như chúng ta đã thấy trong Chương `1`, động lực chi phối chủ yếu đằng sau lộ trình này là sự giảm đều đặn kích thước linh kiện, hay kích thước đặc trưng tối thiểu. Sự giảm kích thước đặc trưng này tương ứng với hệ số `0,7X` theo kích thước tuyến tính, hoặc sự giảm diện tích cần thiết cho mỗi transistor đi `50%` xấp xỉ mỗi ba năm. Cũng đáng chú ý trong bảng là các kích thước đặc trưng tối thiểu được trích dẫn phổ biến nhất trong `NTRS` (các giá trị in đậm trong bảng tương ứng với các vạch và khe dày đặc trong chip `DRAM`) thực ra không nhỏ bằng các vạch cô lập (`isolated lines`) — tức cổng `MOS` — cần có trên các chip vi xử lý (`MPU`). Các đặc trưng này nói chung nhỏ hơn `20% - 30%` so với "kích thước đặc trưng tối thiểu" thường được trích dẫn. Các đặc trưng tối thiểu không những phải giảm về kích thước trung bình theo từng thế hệ công nghệ, mà độ biến thiên của các kích thước đặc trưng này cũng phải giảm theo thời gian. Nói chung, kiểm soát `CD (critical dimension)` được yêu cầu vào khoảng `10%` của kích thước đặc trưng nhỏ nhất. Yêu cầu này thường được biểu diễn dưới dạng kiểm soát `3σ` (`3` độ lệch chuẩn của quần thể kích thước đặc trưng phải nằm trong phạm vi `10%` quy định của giá trị trung bình).

Độ chính xác đặt vị trí hay căn chỉnh tương ứng cho các đặc trưng này (`overlay`) duy trì ở mức khoảng `1/3` kích thước đặc trưng tối thiểu đối với mỗi thế hệ công nghệ. Kích thước chip được `NTRS` dự đoán sẽ tăng đáng kể theo thời gian. Do đó, diện tích in quang khắc tương ứng (`field size`) cũng cần tăng lên để có thể in ít nhất một chip trong mỗi trường phơi. Thông thường, khoảng `1/3` tổng chi phí chế tạo wafer được tiêu thụ bởi quang khắc. Vì vậy, với chi phí chế tạo wafer khoảng `$1000` cho một wafer `8"`, chỉ có thể dành vài trăm đô la cho quang khắc. Các thiết bị phơi chiếu wafer hiện nay có giá khoảng `$10M`, và do đó phải có khả năng in ở mức cỡ `50` wafer mỗi giờ để đáp ứng các mục tiêu chi phí này.

---

> **[Bảng thông số]**

| Hạng mục | 1997 | 1999 | 2003 | 2006 | 2009 | 2012 |
|---|:---:|:---:|:---:|:---:|:---:|:---:|
| Năm giao lô `DRAM` đầu tiên | 1997 | 1999 | 2003 | 2006 | 2009 | 2012 |
| Số bit/Chip `DRAM` | 256M | 1G | 4G | 16G | 64G | 256G |
| **Kích thước đặc trưng tối thiểu (nm)** | | | | | | |
| &emsp;Vạch cô lập (`MPU`) | 200 | 140 | 100 | 70 | 50 | 35 |
| &emsp;**Vạch dày đặc (`DRAM`)** | **250** | **180** | **130** | **100** | **70** | **50** |
| &emsp;`Contacts` | 280 | 200 | 140 | 110 | 80 | 60 |
| Kiểm soát `Gate CD` `3σ` (nm) | 20 | 14 | 10 | 7 | 5 | 4 |
| Căn chỉnh (`mean + 3σ`) (nm) | 85 | 65 | 45 | 35 | 25 | 20 |
| Độ sâu tiêu cự — `Depth of Focus` (µm) | 0,8 | 0,7 | 0,6 | 0,5 | 0,5 | 0,5 |
| Mật độ khuyết tật (mỗi lớp/m²) @ Kích thước khuyết tật (nm) | 100 @ 80 | 80 @ 60 | 60 @ 40 | 50 @ 30 | 40 @ 20 | 30 @ 15 |
| Kích thước chip `DRAM` (mm²) | 280 | 400 | 560 | 790 | 1120 | 1580 |
| Kích thước chip `MPU` (mm²) | 300 | 360 | 430 | 520 | 620 | 750 |
| Kích thước trường — `Field Size` (mm) | 22×22 | 25×32 | 25×36 | 25×40 | 25×44 | 25×52 |
| Công nghệ phơi chiếu | 248nm `DUV` | 248nm `DUV` | 248nm hoặc 193nm `DUV` | 193nm `DUV` hoặc ? | 193nm `DUV` hoặc ? | ? |
| Số lượng `mask` tối thiểu | 22 | 22/24 | 24 | 24/26 | 26/28 | 28 |

**Bảng 5.1:** Các yêu cầu quang khắc đối với các thế hệ tương lai của công nghệ silicon `[5.1]`.

---

Quang khắc quang học chắc chắn sẽ được sử dụng xuyên suốt các thế hệ `0,18` và `0,13 µm`, và nhiều khả năng còn có thể được mở rộng đến cả thế hệ `0,1 µm`. Sau điểm đó, tồn tại sự bất định đáng kể, vì những lý do mà chúng ta sẽ thảo luận chi tiết trong chương này. Các ứng viên tiềm năng để thay thế quang khắc quang học bao gồm `x-ray`, ghi trực tiếp bằng chùm điện tử (`e-beam direct write`), `projection e-beam` và tử ngoại cực hạn (`EUV`), mỗi công nghệ trong số đó đang được nghiên cứu theo nhiều cách tiếp cận khác nhau. Hai công nghệ sau hiện nay là các "ứng viên thắng cuộc" có khả năng nhất, nhưng vẫn còn nhiều tranh luận đáng kể về việc kỹ thuật nào (nếu có) trong số này sẽ chứng tỏ là thành công trong chế tạo vượt quá `0,1 µm`. Sự bất định này có lẽ là thách thức đơn lẻ lớn nhất mà ngành công nghiệp bán dẫn hiện nay đang phải đối mặt xét về việc tiếp tục duy trì các xu hướng lịch sử được biểu diễn bởi `NTRS`.

Trong chương này, chúng ta sẽ khảo sát hai lĩnh vực chính gắn với quá trình quang khắc. Lĩnh vực thứ nhất là hệ thống phơi chiếu dùng để in các mẫu lên wafer. Chúng ta sẽ tập trung vào các hệ thống phơi chiếu quang học vì chúng hiện đang chi phối ngành công nghiệp. Các hệ thống điển hình ngày nay sử dụng in chiếu thu nhỏ kiểu `"step and repeat"` hoặc `"step and scan"` với các hệ thấu kính phức tạp. Lĩnh vực chính thứ hai mà chúng ta sẽ khảo sát là bản thân vật liệu `photoresist`. Ở đây, các vấn đề chủ yếu là độ nhạy, độ phân giải và độ bền công nghệ (`ruggedness`). Các `resist` điển hình hiện nay là các vật liệu hữu cơ nền carbon đã được thiết kế tối ưu cho hiệu năng trong chế tạo `IC`.

---

## 5.2 Sự phát triển lịch sử và các khái niệm cơ bản

Toàn bộ quá trình quang khắc được minh họa về mặt khái niệm trong **Hình 5.1**. Các mẫu tạo nên các lớp khác nhau trong một mạch tích hợp được thiết kế bằng các hệ thống thiết kế có sự hỗ trợ của máy tính (`CAD`). Ngày nay, các hệ thống này chứa nhiều khả năng tiên tiến giúp cải thiện đáng kể hiệu quả thiết kế các chip có nhiều triệu linh kiện. Các thư viện của những thiết kế trước đó đã được biết là hoạt động đúng thường sẵn có; từ đó các chức năng hoặc mạch cơ bản có thể được cắt và dán vào các thiết kế mới. Các công cụ phần mềm được dùng để hỗ trợ định tuyến hoặc đi dây các kết nối giữa các khối chức năng. Các công cụ bổ sung kiểm tra thiết kế để bảo đảm rằng không có vi phạm nào đối với các quy tắc thiết kế. Và cuối cùng, các công cụ mô phỏng ở mức mạch và mức hệ thống sẵn có để dự đoán hiệu năng của thiết kế mới.

---

**Hình 5.1:** Quy trình quang khắc từ thiết kế `mask` đến in lên wafer.

---

Một khi thiết kế đã hoàn tất và sẵn sàng chuyển đến cơ sở chế tạo, thông tin cho mỗi mức `mask` được chuyển tới một máy chế tạo `mask`, là máy tạo mẫu dùng chùm điện tử hoặc laser. Mẫu cho mỗi `mask` được ghi trực tiếp lên một `mask blank` bằng cách sử dụng chùm điện tử quét hoặc chùm laser quét. Bản thân `mask` thường là một tấm `fused silica` được phủ một lớp mỏng (`≈ 80 nm`) `chromium` và một lớp `photoresist`. Một lớp phủ chống phản xạ mỏng (`ARC`) (`10 - 15 nm`) cũng thường được dùng giữa lớp chrome và lớp `resist` để ngăn các phản xạ từ lớp chrome, vốn có thể làm suy giảm độ phân giải mẫu. Chùm điện tử hoặc chùm laser sẽ phơi lớp `resist`, sau đó lớp này được hiện hình và dùng làm `mask` khắc để chuyển mẫu `mask` vào lớp chrome. Lớp chrome thường được khắc ướt vì quá trình này đơn giản, mặc dù khắc khô có thể sẽ được sử dụng rộng rãi hơn trong tương lai khi kích thước tiếp tục giảm. Có thể duy trì kiểm soát kích thước chặt chẽ vì lớp chrome rất mỏng. Sau khi chrome được khắc xong, lớp `photoresist` được loại bỏ. Đế `fused silica` có các bề mặt được đánh bóng rất kỹ để ánh sáng không bị tán xạ khi đi qua `mask`, và lý tưởng là có hệ số giãn nở nhiệt nhỏ để kích thước `mask` ổn định trước các biến thiên nhiệt độ nhỏ. Cũng hiển nhiên là các vùng trong suốt của `mask`, nơi lớp chrome đã bị khắc bỏ, phải có độ truyền qua cao tại bước sóng ánh sáng được sử dụng trong hệ thống phơi chiếu wafer. Điều này trong thực tế ngày càng khó đạt được hơn khi bước sóng phơi đi sâu hơn vào vùng `UV` để đạt độ phân giải cao hơn. Mặc dù vật liệu `mask` (về cơ bản là `SiO₂`) có độ rộng vùng cấm lớn (`≈ 9 eV`), các tạp chất vết trong thủy tinh có thể làm suy giảm độ trong suốt quang học vì chúng có thể hấp thụ ánh sáng tại các bước sóng ngắn này.

Thông thường, `mask` được chế tạo với các kích thước mẫu lớn hơn `4X` đến `5X` so với các đặc trưng thực sự mong muốn trên wafer, vì hệ thống phơi chiếu wafer sẽ thu nhỏ ảnh với cùng hệ số đó. Sự thu nhỏ ảnh (`demagnification`) trong hệ thống phơi chiếu wafer làm cho `mask` dễ chế tạo hơn và dễ kiểm tra khuyết tật hơn. Đây là một bước cực kỳ quan trọng vì bất kỳ khuyết tật nào trên `mask` sẽ được ghi ảnh trực tiếp lên mọi wafer được phơi bằng `mask` đó và góp phần làm suy giảm `yield`. Vì các hệ thống phơi kiểu `"step and repeat"` điển hình chỉ phơi một vùng bằng một hoặc hai chip tại một thời điểm, một khuyết tật trên `mask` được in lên wafer có thể dễ dàng làm cho `yield` bằng không. Việc kiểm tra `mask` được thực hiện bằng cách so sánh mẫu chrome trên `mask` với một mẫu giống hệt khác khi có hai hay nhiều mẫu chip trên `mask`. Nếu mẫu `mask` lớn đến mức chỉ có một mẫu chip hiện diện, việc so sánh có thể được thực hiện với cơ sở dữ liệu trong hệ thống `CAD` đã dùng để tạo `mask`. Các khuyết tật thường có thể được sửa chữa ở giai đoạn này, hoặc bằng cách loại bỏ các vùng chrome không mong muốn bằng bóc tách laser (`laser ablation`) hay chùm ion, hoặc bằng cách lắng đọng thêm chrome để lấp các lỗ kim (`pinholes`). Một khi `mask` đã được kiểm tra, và được sửa nếu cần, nó thường được bảo vệ khỏi sự nhiễm bẩn về sau bởi các hạt bụi bằng một màng trong suốt mỏng (`pellicle`) được căng trên một khung kim loại phía trên mặt có chrome của `mask`. `Pellicle` thường được làm từ `nitrocellulose` với chiều dày vài micron. Vì `pellicle` được đặt lệch khỏi `mask`, các hạt bụi rơi lên `pellicle` trong quá trình sử dụng sẽ bị lệch tiêu điểm trên wafer và do đó thường sẽ không được in ra. Thông thường `pellicle` có thể được gắn cách `mask` vài `mm`. Vì độ sâu tiêu cự của các hệ thống phơi hiện đại chỉ vào cỡ vài `µm`, các hạt bụi có kích thước tới `100 µm` sẽ không in lên wafer trong quá trình phơi.

Việc ghi mẫu `mask` thực tế thường được thực hiện bằng một máy tạo mẫu dùng laser hoặc chùm điện tử như minh họa trong **Hình 5.1**. Các máy này quét một chùm laser hoặc một chùm điện tử theo mẫu `X-Y` kiểu `raster` trên `mask`, với chùm tia được đóng/ngắt khi cần thiết để tạo ra mẫu `mask` thích hợp. Nói chung, kích thước chùm tia vào cỡ `0,1 - 0,5 µm` đối với các hệ `e-beam` và hơi lớn hơn đối với các hệ dựa trên laser, đủ để ghi các `mask` `4X` hoặc `5X` cho các `stepper` hiện nay. Khi các kích thước đặc trưng tối thiểu tiếp tục giảm, kích thước chùm tia cũng sẽ phải thu nhỏ theo để tạo ra các `mask` có độ phân giải thích hợp. Có lẽ khá hiển nhiên rằng hệ `e-beam` có thể được dùng trực tiếp để ghi ảnh lên wafer chỉ bằng cách đặt lớp `resist` nhạy điện tử lên wafer thay vì lên `mask`. Lý do điều này không được thực hiện trong sản xuất khối lượng lớn đơn giản là vì thông lượng wafer sẽ quá chậm. Các máy tạo mẫu `e-beam` điển hình sẽ cần hàng chục phút để phơi một wafer hoàn chỉnh. Điều này chậm hơn nhiều so với các `stepper` quang học vốn điển hình có thông lượng vào cỡ `50` wafer mỗi giờ. Tuy nhiên, khi kích thước linh kiện tiếp tục thu nhỏ, các cách tiếp cận `e-beam` đối với phơi chiếu wafer ít nhất cũng cung cấp được độ phân giải yêu cầu, nếu có thể tìm ra phương tiện để cải thiện thông lượng. Chúng ta sẽ quay lại vấn đề này ở phần sau của chương.

Thông tin mẫu được chuyển lên wafer bằng cách in mẫu `mask` vào một lớp `photoresist` trên bề mặt wafer. Nói chung ngày nay việc này được thực hiện bằng một hệ thống phơi chiếu chiếu ảnh (`projection exposure system`) như cũng được minh họa trong **Hình 5.1**. Ánh sáng từ một nguồn cường độ cao được chuẩn trực và cho đi qua `mask`. Mỗi vùng trong suốt trên `mask` truyền ánh sáng, sau đó ánh sáng này được thu gom và hội tụ bởi một hệ thấu kính thứ hai. Hệ thấu kính thứ hai này cũng có tác dụng thu nhỏ kích thước ảnh đi `4X - 5X`. Trường nhìn của các hệ như vậy điển hình chỉ vài `cm` mỗi cạnh, do đó chỉ có một vài chip được in trong mỗi lần phơi. Wafer được dịch chuyển cơ học ("`stepped`") đến trường phơi kế tiếp và quá trình được lặp lại, vì vậy các hệ này thường được gọi là thiết bị `"step and repeat"` hay đơn giản là `steppers`. Trong một số hệ (`"scanners"`), một khe sáng hẹp được tạo bởi hệ nguồn sáng và `mask` cùng wafer được quét cơ học đồng thời sao cho ảnh của `mask` được quét qua wafer. Lưu ý rằng trong các hệ kiểu này, hệ cơ khí phải quét `mask` nhanh hơn wafer `4X` hoặc `5X`, tương ứng với hệ số thu nhỏ quang học. `Scanners` làm tăng đáng kể kích thước trường, tối đa tới giới hạn kích thước của `mask`, ít nhất theo phương quét.

Sẽ thuận tiện nếu tách quá trình quang khắc thành ba phần. Phần thứ nhất, và là phần đơn giản nhất, là nguồn sáng dùng để tạo ra các photon mà cuối cùng sẽ phơi `resist`. Mặc dù điều này có vẻ là một nhiệm vụ đơn giản, quang khắc độ phân giải cao hơn đòi hỏi các photon có bước sóng ngắn hơn và điều này làm cho vấn đề nguồn sáng trở nên phức tạp hơn. Phần thứ hai của quá trình quang khắc là hệ thống phơi chiếu tạo ảnh `mask` lên bề mặt wafer. Hệ thống này tạo ra cái được gọi là `aerial image` (**Hình 5.2**) tại bề mặt trên cùng của lớp `resist`. Ảnh này về cơ bản là phân bố bức xạ quang học tác động lên bề mặt trên của `resist`. Trong ví dụ ở **Hình 5.2**, một `resist` dương (`positive resist`) được minh họa vì cực tính `resist` này đại diện cho phần lớn các ứng dụng chế tạo ngày nay. Các photon tới tác động lên `resist` tại các vùng sáng, làm thay đổi các tính chất của nó tại các vùng đó. Phân bố cường độ quang học ba chiều xuyên qua lớp `photoresist` tạo ra một `latent image` (ảnh tiềm ẩn) ba chiều của mẫu `mask`, có thể được hiện hình sau đó. `Positive resist` đã phơi trong ví dụ này sẽ hòa tan trong dung dịch hiện hình `resist`. Sau khi hiện hình, `resist` trong ví dụ này được dùng như một `mask` khắc để lớp liên kết cục bộ `TiN` có thể bị khắc bỏ tại những nơi không mong muốn (xem Hình `2.37` trong `process flow` ở Chương `2`). Phần thứ ba của quá trình quang khắc bao gồm tất cả các vấn đề gắn với bản thân `resist`, phơi, hiện hình, nung (`baking`), v.v.

---

**Hình 5.2:** Tách quá trình quang khắc thành phần phơi chiếu và các đặc trưng trên wafer. Ranh giới phân chia là `aerial image` của `mask`, tức mẫu bức xạ tác động lên bề mặt của `photoresist`. Ví dụ này tương ứng với các Hình `2.36 - 2.37` ở Chương `2`.

---

Do đó, `aerial image` đóng vai trò là ranh giới phân chia giữa các phần chính của hệ thống quang khắc (thiết bị phơi chiếu và `resist`). Nhiệm vụ của thiết bị phơi chiếu là tạo ra `aerial image` tốt nhất có thể. "Tốt nhất" được định nghĩa theo độ phân giải, trường phơi chiếu, độ sâu tiêu cự, độ đồng đều và sự không có sai lệch quang học (`aberrations`) trên toàn trường, cường độ photon, v.v. Nhiệm vụ của `photoresist` là chuyển `aerial image` này thành một bản sao ba chiều dạng màng mỏng của `aerial image` tốt nhất có thể. Ở đây, "tốt nhất" được định nghĩa theo độ chính xác hình học, tốc độ phơi và khả năng chống chịu của `resist` đối với các công đoạn xử lý tiếp theo (`ruggedness`). Trong các phần tiếp theo, chúng ta sẽ xem xét nhiều khái niệm cơ bản gắn với các thiết bị phơi chiếu và `resist`, đồng thời cũng sẽ điểm qua ngắn gọn các vấn đề liên quan đến chính nguồn sáng.

---

### 5.2.1 Nguồn sáng

Có lẽ đối với hầu hết người đọc đều hiển nhiên rằng quang khắc có độ phân giải cao hơn đòi hỏi các photon có bước sóng ngắn hơn. Các hệ thống phơi chiếu hiện đại tạo ra các ảnh bị giới hạn bởi nhiễu xạ, và các hiệu ứng nhiễu xạ liên quan chặt chẽ đến bước sóng của bức xạ phơi. Chúng ta sẽ thảo luận vấn đề này chi tiết hơn trong thời gian ngắn, nhưng trong phần này chúng ta trước tiên xem xét các vấn đề liên quan đến việc tạo ra ánh sáng trong các hệ thống quang khắc hiện đại. Về mặt lịch sử, hầu hết các hệ thống quang khắc đã sử dụng đèn hồ quang (`arc lamps`) làm nguồn sáng chính. Các đèn này thường chứa hơi `Hg` bên trong một bóng thủy tinh kín. Hai điện cực dẫn điện bên trong bóng đèn được cách nhau vài `mm`. Một hồ quang được tạo ra giữa các điện cực bằng cách đặt một điện áp đủ cao để ion hóa khí (thường là vài `kV`). Một khi khí bị ion hóa, nó hoạt động như một plasma, về mặt khái niệm tương tự như các plasma được dùng trong các hệ thống lắng đọng và khắc được mô tả trong Chương `9` và `10`. Trong đèn hồ quang, plasma dẫn điện và bao gồm các ion, electron và các chất trung hòa. Các đèn điển hình dùng cho quang khắc tiêu thụ khoảng một `kW` công suất. Ở nhiệt độ phòng, áp suất hơi `Hg` vào khoảng `1 atm`, nhưng một khi đèn hoạt động, sự tiêu tán công suất nhanh chóng làm tăng nhiệt độ và do đó áp suất bên trong tới `≈ 20 - 40 atm`.

Phát xạ ánh sáng xảy ra qua hai quá trình. Các electron tự do trong plasma có nhiệt độ hiệu dụng vào khoảng `40.000 K` và phát xạ bức xạ vật đen theo Định luật Planck. Bước sóng tương ứng với nhiệt độ này nằm rất sâu trong vùng tử ngoại và vượt quá độ rộng vùng cấm của `fused silica` dùng để tạo bóng thủy tinh của đèn. Do đó bức xạ này hầu hết bị hấp thụ trước khi thoát ra khỏi đèn.

Nguồn phát xạ ánh sáng thứ hai đến từ chính các nguyên tử `Hg`. Các va chạm trong khí giữa các electron tự do và các nguyên tử `Hg` cung cấp năng lượng cho một số electron trong nguyên tử `Hg`, nâng chúng lên các mức năng lượng cao hơn. Khi các electron này trở về các trạng thái năng lượng thấp hơn, chúng bức xạ các photon tại các năng lượng (tần số) xác định, đặc trưng cho các mức năng lượng được phép trong nguyên tử `Hg`. Quá trình này rất giống với quá trình được minh họa trong Hình `4.18` ở Chương `4`, nơi chúng ta đã thảo luận về việc sử dụng các chuyển dời năng lượng này để nhận dạng các nguyên tố cụ thể từ đó các photon được phát ra. Trong trường hợp `Hg`, có phát xạ mạnh tại một số bước sóng `UV`. Hầu hết các `stepper` sử dụng một bước sóng đơn bằng cách đơn giản là lọc bỏ các phát xạ không mong muốn. Các hệ thống quang học phức tạp trong các thiết bị phơi chiếu này dễ thiết kế hơn nhiều nếu chúng chỉ cần hội tụ một bước sóng duy nhất. Hai bước sóng thường được sử dụng là `436 nm` (vạch `g`) và `365 nm` (vạch `i`). Hầu hết các thiết bị phơi chiếu đầu những năm `1990` sử dụng vạch `g`. Tuy nhiên, khi các chiều rộng vạch thu nhỏ, việc sử dụng vạch `i` đã trở nên phổ biến hơn ngày nay do độ phân giải tốt hơn mà nó cung cấp. Một số thiết bị phơi chiếu, đặc biệt là các máy in tiếp xúc và máy in tiếp cận đơn giản, đôi khi sử dụng ánh sáng có bước sóng rộng hơn (một số vạch từ nguồn `Hg`) để phơi vì không có quang học hội tụ trong các hệ thống này.

Các `stepper` vạch `i` đã chi phối sản xuất cho thế hệ công nghệ `0,35 µm`. Các thế hệ vượt quá `0,35 µm` đòi hỏi bước sóng phơi ngắn hơn và các nguồn sáng mới. Các nguồn sáng có cường độ cao nhất trong phần tử ngoại sâu (`deep UV`) của phổ là các laser excimer. Hai loại có ý nghĩa đặc biệt đối với quang khắc là `KrF` (`248 nm`) và `ArF` (`193 nm`). Trong các laser excimer, hai nguyên tố hiện diện mà thông thường không phản ứng với nhau ở trạng thái không kích thích (thường là một khí hiếm và một hợp chất chứa halogen). Tuy nhiên, nếu các nguyên tố này (ví dụ `Kr` và `NF₃`) bị kích thích, một phản ứng hóa học tạo thành, ví dụ `KrF`, là có thể xảy ra. Khi phân tử bị kích thích trở về trạng thái cơ bản của nó, một photon được phát ra trong vùng tử ngoại sâu và phân tử bị phân hủy. Do đó năng lượng phải được cung cấp liên tục, thường từ một phóng điện xung nội bộ, để bổ sung quần thể của các chất bị kích thích. Thông thường nguồn laser được kích xung ở tần số vài trăm `Hz` và nói chung khoảng `100` xung được sử dụng tại mỗi vị trí phơi chiếu trên wafer để giảm thiểu nhiễu `speckle`. Tổng năng lượng vài trăm `mJ` được cung cấp cho mỗi vị trí phơi chiếu. Trong các `stepper`, năng lượng này được hội tụ lên diện tích wafer vài `cm²`, cung cấp thời gian phơi hợp lý. Một số vấn đề tồn tại với các nguồn phơi này, bao gồm độ tin cậy và tuổi thọ của laser, độ trong suốt của các thành phần quang học trong hệ thống thấu kính tại các bước sóng này, và việc tìm các `resist` phù hợp. Các vấn đề này đã được giải quyết ở `248 nm` (`KrF`) và nguồn này hiện đang được sử dụng trong sản xuất thương mại cho các thế hệ `0,25 µm` và `0,18 µm`. `ArF` là nguồn có khả năng nhất cho các thế hệ công nghệ `0,13 µm` và `0,10 µm`. Tại thời điểm này, bức tranh kém rõ ràng hơn nhiều cho các thế hệ vượt quá `0,1 µm`.

---

### 5.2.2 Các hệ thống phơi chiếu wafer

Bây giờ chúng ta xem xét chi tiết hơn một trong những yếu tố then chốt trong quang khắc hiện đại, đó là hệ thống dùng để tạo ra `aerial image` tại bề mặt `photoresist`. Có ba loại chung của thiết bị phơi chiếu wafer quang học: hệ thống tiếp xúc (`contact`), hệ thống tiếp cận (`proximity`) và hệ thống chiếu ảnh (`projection`), mặc dù chỉ có loại sau là được sử dụng rộng rãi trong sản xuất khối lượng lớn ngày nay. Các hệ thống này được minh họa về mặt khái niệm trong **Hình 5.3**.

---

**Hình 5.3:** Ba phương pháp cơ bản của phơi chiếu wafer.

---

In tiếp xúc (`contact printing`) là quy trình in lâu đời nhất và đơn giản nhất. `Mask` được đặt mặt chrome úp xuống tiếp xúc trực tiếp với lớp `resist` trên wafer. Việc phơi `resist` sau đó diễn ra bằng cách chiếu ánh sáng xuyên qua `mask`. Việc căn chỉnh `mask` với các mẫu đã có trên wafer diễn ra trước khi phơi, bằng cách quan sát cả mẫu trên `mask` lẫn mẫu trên wafer qua kính hiển vi với `mask` cách wafer một khoảng nhỏ. Các hệ thống in tiếp xúc thực tế có khả năng in có độ phân giải cao vì với `mask` và wafer tiếp xúc nhau, các hiệu ứng nhiễu xạ được giảm thiểu. Ngoài ra, các máy để thực hiện in tiếp xúc tương đối không đắt. Tuy nhiên, các loại hệ thống này không thể được sử dụng trong sản xuất khối lượng lớn các chip phức tạp vì một lý do rất đơn giản. Sự tiếp xúc cứng giữa `mask` và wafer dẫn đến hư hỏng cả `mask` lẫn lớp `resist` và do đó dẫn đến mật độ khuyết tật cao. Các `yield` chip kết quả không tương thích với sản xuất kinh tế của các chip ngày nay. Tuy nhiên, các hệ thống in tiếp xúc được sử dụng trong một số ứng dụng sản xuất nơi mà khối lượng thấp hoặc kích thước chip nhỏ làm cho kinh tế học của các hệ thống này hấp dẫn hơn.

In tiếp cận (`proximity printing`) về cơ bản giải quyết các vấn đề khuyết tật liên quan đến in tiếp xúc, vì `mask` và wafer được giữ cách nhau `5 - 25 µm`. Tuy nhiên, các hệ thống này cũng không phù hợp để sản xuất hầu hết các chip ngày nay vì sự cách ly giữa `mask` và wafer làm suy giảm độ phân giải của các mẫu được in do các hiệu ứng nhiễu xạ. Chúng ta sẽ lượng hóa các hiệu ứng này trong thời gian ngắn, nhưng trong thực tế không thể in các đặc trưng nhỏ hơn vài `µm` với phơi chiếu `UV` và các khoảng cách vào cỡ `20 µm`. Điều thú vị là, độ phân giải của các hệ thống này cải thiện khi bước sóng phơi giảm và các hệ thống quang khắc `x-ray` có thể sử dụng in tiếp cận và đạt độ phân giải cao vì bước sóng phơi rất ngắn (`1 - 2 nm`). Chúng ta sẽ quay lại các hệ thống `x-ray` ở cuối chương này. Cả hệ thống tiếp xúc lẫn hệ thống tiếp cận đều yêu cầu `mask` tỷ lệ `1X`, khó chế tạo hơn so với `mask` cho các hệ thống thu nhỏ ảnh.

Phương pháp phổ biến nhất của phơi chiếu wafer ngày nay là in chiếu ảnh (`projection printing`). Các hệ thống này cung cấp độ phân giải cao nhưng không có các vấn đề khuyết tật của in tiếp xúc. Trong các thiết bị phơi chiếu chiếu ảnh, `mask` được cách ly vật lý khỏi wafer và một hệ thống quang học được dùng để tạo ảnh `mask` lên wafer. Điều này rõ ràng giải quyết các vấn đề khuyết tật liên quan đến in tiếp xúc. Độ phân giải của các máy in chiếu ảnh nói chung bị giới hạn bởi các hiệu ứng nhiễu xạ mà chúng ta sẽ mô tả chi tiết. Nói chung, hệ thống quang học thu nhỏ ảnh `mask` đi `4X` đến `5X`, có nghĩa là chỉ có một phần nhỏ của wafer được in trong mỗi lần phơi. Điển hình các `stepper` như vậy hiện nay có khả năng in các đặc trưng `0,25 µm` trên một trường phơi chiếu vài `cm²` và có thông lượng `25 - 50` wafer mỗi giờ. Chúng cũng có giá nhiều triệu đô la.

### 5.2.2.1 Các cơ sở quang học — truy vết tia và nhiễu xạ

Để hiểu và định lượng các khả năng của các hệ thống phơi chiếu wafer hiện đại, chúng ta sẽ cần xem lại một số khái niệm cơ bản về ánh sáng và các hệ quang học. Có nhiều tài liệu tham khảo tiêu chuẩn về các chủ đề này `[xem, ví dụ, 5.2]`, và người đọc được dẫn tới các tài liệu đó để có cách trình bày chi tiết hơn về các khái niệm được mô tả ở đây. Việc áp dụng các nguyên lý quang học cơ bản vào các hệ thống quang khắc cũng được mô tả chi tiết trong một số sách, ví dụ `[5.3, 5.4]`. Trong phần này, chúng ta sẽ giới thiệu các ý tưởng cơ bản theo cách phần nào mang tính định tính. Trong Mục `5.5`, chúng ta sẽ trình bày định lượng hơn.

Ánh sáng truyền trong không gian dưới dạng sóng điện từ. Khi người ta quan tâm đến ứng xử của một hệ quang học mà trong đó mọi kích thước đều rất lớn so với bước sóng ánh sáng, ánh sáng thường có thể được xem như các hạt truyền theo các đường thẳng giữa các thành phần quang học. Điều này đơn giản hóa bài toán thành bài toán “truy vết tia” (`ray tracing`). Chẳng hạn, trong các hệ quang khắc chiếu ảnh (`projection lithography systems`), cách tiếp cận này thường có thể được dùng để mô tả nguồn quang học và thấu kính tụ (`condenser lens`), nhưng nó không còn đúng khi ánh sáng đi qua `mask` vì kích thước đặc trưng trên `mask` có thể so sánh được với bước sóng ánh sáng. Để hiểu ứng xử của ánh sáng khi nó đi qua `mask`, thấu kính vật kính (`objective lens`) và tới wafer, chúng ta phải kể đến bản chất sóng của ánh sáng. Hiệu ứng quan trọng nhất mà chúng ta phải xét đến là nhiễu xạ.

Các hiệu ứng nhiễu xạ xuất hiện vì ánh sáng trên thực tế không truyền theo các đường thẳng. Nhiều thí nghiệm đơn giản có thể chứng minh sự thật này. **Hình 5.4** minh họa sự truyền của ánh sáng qua một khẩu độ nhỏ. Mẫu ánh sáng tác động lên màn chắn (mặt phẳng ảnh) phủ lên một vùng lớn hơn nhiều so với vùng có thể giải thích chỉ bằng cách vẽ các đường thẳng (`ray tracing`) để mô tả sự lan truyền của ánh sáng. Trên thực tế, khẩu độ càng nhỏ thì ảnh trên màn càng trải rộng hơn. Điều này rất giống với tình huống mà chúng ta gặp trong quang khắc hiện đại, nơi ánh sáng đi qua một `mask` có các khẩu độ (các vùng trong suốt) với kích thước vào cỡ bước sóng ánh sáng. (Chúng ta thực ra đã minh họa các hiệu ứng này trong các Hình `5.1` và `5.3` bằng cách cho thấy ánh sáng lan rộng ra sau khi đi qua `mask`, nhưng đã không giải thích vì sao điều này xảy ra trong mối liên hệ với các hình đó.)

---

**Hình 5.4:** Ví dụ đơn giản về các hiệu ứng nhiễu xạ. Ánh sáng đi qua một khẩu độ hẹp. Ảnh được hình thành phủ lên một vùng lớn hơn nhiều so với vùng có thể giải thích dựa trên truy vết tia đường thẳng đơn giản.

---

Hãy xét **Hình 5.5**. Một sóng phẳng được minh họa đang lan truyền trong không gian, không bị cản trở trong phần a), và đi qua một khẩu độ trong phần b). Nguyên lý Huygens-Fresnel có thể được dùng để dựng mặt sóng theo vị trí khi nó lan truyền. Nguyên lý này phát biểu rằng mọi điểm không bị che chắn của một mặt sóng tại một thời điểm cho trước đều đóng vai trò như một nguồn phát ra sóng cầu thứ cấp có cùng tần số với sóng sơ cấp. Biên độ của trường quang học có thể được xác định bằng cách chồng chập tất cả các sóng con này, có xét tới biên độ tương đối và pha của chúng. Trong phần a), sự chồng chập này đơn giản dẫn đến một sóng phẳng lan truyền. Trong phần b), chỉ các điểm nguồn trong khẩu độ mới đóng vai trò là các nguồn của các sóng con Huygens, và mẫu lan truyền thu được ở phía sau khẩu độ có bao hàm nhiễu xạ. Như các mũi tên trong phần b) cho thấy, ánh sáng lan rộng ra sau khẩu độ. Trên thực tế, khẩu độ càng nhỏ thì ánh sáng càng lan rộng hơn, bởi vì có ít sóng con hơn có thể đi qua khẩu độ và do đó sự lan truyền mang tính cầu ở phía sau khẩu độ trở nên nổi bật hơn.

---

**Hình 5.5:** Sự lan truyền của một sóng phẳng trong a) không gian tự do và b) qua một khẩu độ nhỏ, minh họa việc sử dụng Nguyên lý Huygens-Fresnel để dựng mặt sóng khi nó lan truyền.

---

Nhiễu xạ có thể được hình dung đơn giản như sự “uốn cong” của ánh sáng khi nó đi qua một khẩu độ. Ánh sáng đi qua khẩu độ mang theo thông tin về kích thước và hình dạng của khẩu độ đó. Ví dụ, nếu khẩu độ là một phần của `mask` mà chúng ta muốn in lên một wafer trong lớp `resist`, thì thông tin về kích thước và hình dạng khẩu độ cần phải được ánh sáng mang tới lớp `photoresist` trên wafer. Vấn đề là thông tin này lan rộng trong không gian do nhiễu xạ, và toàn bộ nó phải được thu nhận để truyền tải thông tin hoàn hảo về khẩu độ tới lớp `resist` trên wafer. **Hình 5.6** minh họa điều này theo cách định tính. Do kích thước hữu hạn của nó, thấu kính hội tụ chỉ thu nhận được một phần của toàn bộ mẫu nhiễu xạ gắn với ánh sáng đi qua khẩu độ. Phần ánh sáng bị nhiễu xạ tới các góc lớn hơn mang theo thông tin về các chi tiết tinh hơn của khẩu độ, và do đó chính các chi tiết này sẽ mất đi trước tiên khi một thấu kính có kích thước hữu hạn được dùng để thu và hội tụ ánh sáng.

---

**Hình 5.6:** Ví dụ định tính về việc một khẩu độ nhỏ được tạo ảnh.

---

Ảnh thực tế được tạo ra trong ví dụ đơn giản này được trình bày trong **Hình 5.7** đối với một khẩu độ tròn nhỏ, và được gọi là đĩa Airy (`Airy’s disk`) theo tên Sir George Biddell Airy, người đầu tiên suy ra biểu thức mô tả cực đại cường độ trung tâm. Cực đại trung tâm xấp xỉ ảnh của khẩu độ tròn. Do các hiệu ứng nhiễu xạ, ảnh bao gồm một đĩa sáng ở giữa được bao quanh bởi một chuỗi các vòng mờ. Cường độ ảnh có thể được mô tả toán học bằng các hàm Bessel, và kích thước xấp xỉ của ảnh được cho bởi

---

> **[Công thức toán]**
>
> $$
> \text{Khoảng cách tới cực tiểu thứ nhất}
> =
> \frac{1.22\lambda f}{d}
> \tag{5.1}
> $$

---

trong đó `d` là đường kính của thấu kính hội tụ, `f` là tiêu cự và `\lambda` là bước sóng của ánh sáng. Lưu ý rằng một nguồn điểm chỉ tạo ra một ảnh điểm nếu `d → ∞` (hoặc nếu `\lambda → 0` hay `f → 0`).

Người ta thường phân biệt hai loại nhiễu xạ, nhiễu xạ Fresnel hay nhiễu xạ trường gần (`near field diffraction`) và nhiễu xạ Fraunhofer hay nhiễu xạ trường xa (`far field diffraction`). Cả hai về cơ bản đều do cùng một nguyên nhân — bản chất sóng của ánh sáng. Trong nhiễu xạ Fresnel, mặt phẳng ảnh nằm gần khẩu độ. Ánh sáng truyền trực tiếp từ khẩu độ tới mặt phẳng nơi ảnh được hình thành, như trong **Hình 5.4**, mà không có hệ thấu kính xen giữa. Trong nhiễu xạ Fraunhofer, ảnh ở xa khẩu độ và thông thường một thấu kính được đặt giữa khẩu độ và mặt phẳng ảnh để thu và hội tụ ảnh, như trong **Hình 5.6**. Trong các hệ quang khắc hiện đại, nhiễu xạ Fresnel áp dụng cho các hệ phơi chiếu tiếp xúc (`contact`) và tiếp cận (`proximity`), còn nhiễu xạ Fraunhofer áp dụng cho các hệ chiếu ảnh (`projection`), điều này sẽ trở nên hiển nhiên khi xem xét **Hình 5.3**. Các mô tả toán học và các mô hình chi tiết đã được phát triển cho cả hai miền này. Các công cụ mô phỏng mạnh dựa trên các mô hình này cũng đã được phát triển, cho phép tính toán `aerial image` được hình thành bởi hệ thống phơi chiếu wafer. Chúng ta sẽ thảo luận các vấn đề này chi tiết hơn trong Mục `5.5`.

---

**Hình 5.7:** Cường độ ảnh của một khẩu độ tròn trong mặt phẳng ảnh (mẫu nhiễu xạ Fraunhofer). Cường độ được phác dọc theo bất kỳ đường kính nào ở bên trái. Mẫu ở bên phải minh họa ảnh `2D`. Ảnh do J. Goodman cung cấp. In lại với sự cho phép của McGraw Hill `[5.2]`.

---

### 5.2.2.2 Các hệ chiếu ảnh (`projection systems`) — nhiễu xạ Fraunhofer

Hiệu năng của các máy in chiếu ảnh thường được đặc trưng theo một số tham số cơ bản như độ phân giải (`resolution`), độ sâu tiêu cự (`depth of focus`), trường nhìn (`field of view`), hàm truyền điều biến (`modulation transfer function`, `MTF`), độ chính xác căn chỉnh (`alignment accuracy`), thông lượng (`throughput`), v.v. Ít nhất bốn đại lượng đầu tiên trong số này liên hệ trực tiếp với các tính chất cơ bản của các hệ quang học, mà chúng ta sẽ thảo luận trong phần này. Hai vấn đề cuối cùng gắn nhiều hơn với thiết kế cơ khí của hệ thống.

Hãy xét **Hình 5.8**, trong đó bây giờ ta tưởng tượng rằng có hai nguồn điểm ở gần nhau mà ta đang cố gắng tạo ảnh. Ví dụ, đây có thể là hai đặc trưng nhỏ kề nhau trên một `mask` mà chúng ta đang cố in vào `resist` trên một wafer. Chúng có thể ở gần nhau đến mức nào mà vẫn còn được phân giải trong mặt phẳng ảnh? Ảnh được tạo bởi hai nguồn điểm này mỗi ảnh sẽ là một đĩa Airy như đã trình bày trong **Hình 5.7**. Rayleigh gợi ý rằng một tiêu chuẩn hợp lý cho độ phân giải là các cực đại trung tâm của mỗi ảnh điểm nằm tại cực tiểu thứ nhất của ảnh điểm lân cận, với khoảng cách được cho bởi Phương trình `5.1`. Mặc dù định nghĩa này phần nào có tính quy ước, nó hữu ích và đã được chấp nhận rộng rãi. Với định nghĩa này, độ phân giải `R` của thấu kính được cho bởi `[5.5]`

---

> **[Công thức toán]**
>
> $$
> R
> =
> \frac{1.22\lambda f}{d}
> =
> \frac{1.22\lambda f}{n\,2f\sin\alpha}
> =
> \frac{0.61\lambda}{n\sin\alpha}
> \tag{5.2}
> $$
>
> $$
> NA \equiv n\sin\alpha
> \tag{5.3}
> $$
>
> $$
> \therefore\quad
> R = k_1\frac{\lambda}{NA}
> \tag{5.4}
> $$

---

trong đó `n` được đưa vào để giữ tính tổng quát và là chiết suất của môi trường nằm giữa vật và thấu kính (thông thường là không khí với `n = 1` trong các hệ quang khắc). `\alpha` là nửa góc cực đại của phần ánh sáng bị nhiễu xạ có thể đi vào thấu kính, hay góc thu nhận của thấu kính. `\alpha` có thể bị giới hạn bởi chính kích thước vật lý của thấu kính, hoặc bởi một khẩu độ vào (`entrance aperture`) hay `pupil` đặt phía trước thấu kính. `NA` thực sự là thước đo khả năng của thấu kính trong việc thu nhận ánh sáng bị nhiễu xạ. Tính chất này được Ernst Abbe đặt tên là khẩu độ số (`numerical aperture`, `NA`).

---

**Hình 5.8:** Minh họa năng lực phân giải của một thấu kính khi cần tách biệt hai nguồn điểm trong ảnh.

---

Phương trình `5.2` được suy ra từ mẫu nhiễu xạ Fraunhofer của đĩa Airy, và do đó nghiêm ngặt mà nói chỉ áp dụng cho các nguồn điểm. Vì lý do này, hệ số `0,61` thường được thay bằng `k_1` trong Phương trình `5.4`. Trong các hệ quang khắc thực, `mask` chứa nhiều hình dạng khác nhau. Trong thực tế, `k_1` cũng phụ thuộc vào khả năng của hóa học `resist` trong việc phân biệt các đặc trưng nằm gần nhau, vào cấu trúc wafer dưới lớp `resist` (địa hình bề mặt, độ phản xạ, v.v.) và vào hiện tượng mất nét tại mặt phẳng ảnh. Các giá trị `k_1` thực tế đạt được trong các hệ quang khắc quang học là từ `0,6` đến `0,8`.

Hiển nhiên từ Phương trình `5.4` rằng bước sóng phơi ngắn hơn dẫn đến độ phân giải ảnh tốt hơn. Cũng rõ ràng rằng các thấu kính có khẩu độ số lớn hơn cũng đạt được độ phân giải tốt hơn, về cơ bản vì chúng có khả năng thu nhận nhiều hơn phần ánh sáng bị nhiễu xạ và do đó dựng được một ảnh tốt hơn. Ngoài khó khăn trong việc chế tạo các thấu kính lớn hơn (`NA` cao hơn), còn có một bất lợi đáng kể khác của việc dùng thấu kính `NA` cao. Đó là độ sâu tiêu cự của thấu kính, có thể được ước lượng như trong **Hình 5.9**.

Nếu `\delta` là độ chênh chiều dài đường đi trên trục tại giới hạn hội tụ, thì độ chênh chiều dài đường đi đối với một tia từ mép của khẩu độ vào đơn giản là `\delta/\cos\theta`. Tiêu chuẩn Rayleigh đối với độ sâu tiêu cự đơn giản là hai chiều dài này không được khác nhau quá `\lambda/4`. Do đó

---

> **[Công thức toán]**
>
> $$
> \frac{\lambda}{4}
> =
> \frac{\delta}{\cos\theta} - \delta
> \tag{5.5}
> $$

---

Giả sử `\theta` là nhỏ, (điều này không phải là một xấp xỉ tốt trong các hệ `NA` cao),

---

> **[Công thức toán]**
>
> $$
> \frac{\lambda}{4}
> =
> \delta\left[\frac{1}{\cos\theta}-1\right]
> \approx
> \delta\frac{\theta^2}{2}
> \tag{5.6}
> $$
>
> $$
> \theta \approx \sin\theta = \frac{d}{2f} = NA
> \tag{5.7}
> $$
>
> $$
> \therefore\quad
> DOF = \delta = \pm\frac{\lambda}{2(NA)^2}
> =
> \pm k_2\frac{\lambda}{(NA)^2}
> \tag{5.8}
> $$

---

Hệ số `1/2` thường được thay bằng `k_2` trong Phương trình `5.8` vì giá trị `1/2` là thích hợp tại giới hạn phân giải Rayleigh nhưng không xét đến sự gia tăng độ sâu tiêu cự đối với các đặc trưng lớn hơn, cũng như sự phụ thuộc trong thực tế vào các tham số khác như quy trình `resist`.

---

**Hình 5.9:** Hình học dùng để ước lượng độ sâu tiêu cự của một hệ tạo ảnh.

---

## Ví Dụ:

Ước lượng độ phân giải và độ sâu tiêu cự của một `stepper` laser excimer tiên tiến nhất sử dụng nguồn sáng `KrF` (`\lambda = 248 nm`) với `NA = 0,6`. Giả sử `k_1 = 0,75` và `k_2 = 0,5`.

### Lời Giải:

---

> **[Công thức toán - Kết quả tính toán]**
>
> $$
> R = k_1\frac{\lambda}{NA}
> =
> 0.75\left(\frac{0.248}{0.6}\,\mu m\right)
> =
> 0.31\,\mu m
> $$
>
> $$
> DOF = \pm k_2\frac{\lambda}{(NA)^2}
> =
> \pm 0.5\left[\frac{0.248}{(0.6)^2}\,\mu m\right]
> =
> \pm 0.34\,\mu m
> $$

---

Sử dụng thêm các “mẹo” kỹ thuật như chiếu sáng lệch trục (`off-axis illumination`), độ phân giải có thể được đẩy xuống dưới `0,25 µm`, phù hợp với thế hệ `0,25 µm` của `SIA NTRS`. Những cải thiện hơn nữa có thể đạt được thông qua các thiết kế `mask` tinh vi hơn sử dụng các khái niệm như hiệu chỉnh lân cận quang học (`optical proximity correction`) và `phase shift masks`, mà chúng ta sẽ mô tả sau. Độ sâu tiêu cự có cùng bậc độ lớn với chính chiều dày của lớp `resist`, và do đó đòi hỏi địa hình bề mặt rất phẳng cũng như sự chú ý cẩn thận trong `stepper` để giữ cho mặt phẳng ảnh luôn được hội tụ bằng cách điều chỉnh độ cao của wafer so với thấu kính.

---

Còn có một khái niệm cơ bản bổ sung liên quan đến các hệ phơi chiếu quang học sẽ hữu ích đối với chúng ta. Đó là hàm truyền điều biến (`modulation transfer function`, `MTF`) được minh họa trong **Hình 5.10**. Khái niệm này, về mặt nghiêm ngặt, chỉ áp dụng cho chiếu sáng không kết hợp (`incoherent illumination`), và do đó trên thực tế không thật sự áp dụng cho các `stepper` hiện đại, vốn nói chung sử dụng chiếu sáng kết hợp một phần (`partially coherent illumination`). Tuy nhiên, ý tưởng cơ bản này là hữu ích trong việc hiểu các vấn đề quang khắc.

**Hình 5.10:** Khái niệm Hàm Truyền Điều Biến (`MTF`). Một hệ quang khắc tổng quát được trình bày ở trên với `mask` được tạo ảnh lên `photoresist` trên wafer. `MTF` của `mask` gần như lý tưởng (`M = 1`) vì kích thước đặc trưng lớn hơn `4 - 5X` so với các đặc trưng được tạo ảnh trong `resist`, và các hiệu ứng nhiễu xạ là tối thiểu. `MTF` của `aerial image` thấp hơn nhiều (`M ≈ 0,6`) do các hiệu ứng nhiễu xạ trong hệ quang học.

---

**Hình 5.10** trình bày một hệ quang khắc chiếu ảnh tổng quát, trong đó một hệ thấu kính thu nhỏ được dùng để tạo ảnh mẫu `mask` vào `resist`. Vì các hiệu ứng nhiễu xạ chỉ quan trọng sau khi ánh sáng đi qua `mask`, mẫu cường độ quang học khi ánh sáng ra khỏi `mask` sẽ gần như là biểu diễn lý tưởng của `mask`. Tuy nhiên, do các hiệu ứng nhiễu xạ và các sự không lý tưởng khác trong hệ quang học, `aerial image` được tạo ra tại mặt phẳng `resist` sẽ không hoàn toàn là trắng đen lý tưởng. Nếu các đặc trưng ở xa nhau, `aerial image` có thể tiệm cận với ảnh lý tưởng được trình bày ở bên trái trong **Hình 5.10**, nhưng khi các đặc trưng tiến lại gần nhau, `aerial image` sẽ trông giống như hình phác thảo ở bên phải hơn. Như một ví dụ đơn giản, hãy tưởng tượng hai đĩa Airy (**Hình 5.7**) chồng chập một phần lên nhau. Một thước đo hữu ích về chất lượng của `aerial image` là `MTF`, có thể được định nghĩa như sau

---

> **[Công thức toán]**
>
> $$
> MTF = \frac{I_{MAX} - I_{MIN}}{I_{MAX} + I_{MIN}}
> \tag{5.9}
> $$

---

trong đó `I` là cường độ ánh sáng.

`MTF` thực chất là thước đo độ tương phản trong `aerial image` được tạo bởi hệ thống phơi chiếu. Nói chung, một hệ thống phơi chiếu cần đạt được giá trị `MTF` bằng `0,5` hoặc lớn hơn để `resist` phân giải đúng các đặc trưng. Các `resist` tử ngoại sâu (`DUV`) được phát triển gần đây có thể làm việc với các giá trị `MTF` hơi nhỏ hơn.

`MTF` hiển nhiên phụ thuộc vào kích thước đặc trưng trong ảnh và nói chung có ứng xử như minh họa trong **Hình 5.11**. Đối với các đặc trưng lớn, `aerial image` thu được do hệ thống phơi chiếu tạo ra có độ tương phản tốt và `MTF` bằng một. Khi kích thước đặc trưng giảm, các hiệu ứng nhiễu xạ làm `MTF` suy giảm và cuối cùng đạt giá trị không khi các đặc trưng ở gần nhau đến mức không còn độ tương phản nào trong `aerial image`.

---

**Hình 5.11:** Hàm truyền điều biến (`MTF`) theo kích thước đặc trưng trong ảnh.

---

`MTF` cũng bị ảnh hưởng bởi một tham số gọi là độ kết hợp không gian (`spatial coherence`) của nguồn sáng. **Hình 5.12** minh họa khái niệm độ kết hợp không gian. Một nguồn điểm lý tưởng tạo ra ánh sáng mà trong đó các sóng đồng pha tại mọi điểm dọc theo các mặt sóng phát ra. Một thấu kính tụ sau đó có thể chuyển các sóng này thành các sóng phẳng, tất cả đều chiếu vào `mask` tại đúng cùng một góc, như minh họa ở phần trên của hình. Một nguồn như vậy là nguồn kết hợp lý tưởng (`ideal coherent source`). Khi kích thước vật lý của nguồn tăng lên như trình bày ở phần dưới của **Hình 5.12**, ánh sáng được phát ra từ một thể tích thay vì từ một điểm, và các sóng sẽ không hoàn toàn đồng pha ở khắp nơi. Nếu cùng thấu kính tụ đó được dùng để chuyển ánh sáng thành các sóng phẳng, kết quả sẽ là ánh sáng đến `mask` từ nhiều góc độ khác nhau như minh họa. Một nguồn như vậy là nguồn kết hợp một phần (`partially coherent source`). Trong giới hạn khi kích thước nguồn trở nên vô hạn (và thấu kính tụ cũng vô hạn để thu toàn bộ ánh sáng), nguồn sẽ trở thành nguồn hoàn toàn không kết hợp (`completely incoherent`). Một định nghĩa hữu ích về độ kết hợp không gian của các nguồn sáng thực tế dùng trong quang khắc đơn giản là

---

> **[Công thức toán]**
>
> $$
> S = \frac{\text{đường kính nguồn sáng}}{\text{đường kính thấu kính tụ}} = \frac{s}{d}
> \tag{5.10a}
> $$
>
> $$
> S = \frac{NA_{\text{thấu kính tụ}}}{NA_{\text{thấu kính chiếu ảnh}}}
> \tag{5.10b}
> $$

---

---

**Hình 5.12:** Các ví dụ về nguồn sáng kết hợp không gian lý tưởng (trên) và nguồn kết hợp một phần (dưới).

---

Thoạt nhìn có thể dường như chúng ta sẽ chọn một nguồn kết hợp lý tưởng (`s = 0`) cho quang khắc quang học. Tuy nhiên, điều đó không phải là trường hợp tốt nhất vì các lý do sau. Thứ nhất, khi `s → 0`, cường độ quang học cũng tiến về không, dẫn đến thời gian phơi vô hạn để in mẫu `mask` vào `resist`. Thứ hai, `MTF` cũng bị ảnh hưởng bởi giá trị của `s`, và `s = 0` không phải là lựa chọn tối ưu.

Để hiểu điểm thứ hai này, chúng ta cần xem xét các hiệu ứng nhiễu xạ một lần nữa. Nếu ánh sáng đi qua `mask` là kết hợp một phần (tức là đến từ nhiều góc độ khác nhau), thì các mẫu nhiễu xạ thu được từ các đặc trưng trên `mask` sẽ bị trải rộng ra (`smeared out`). Nếu chúng ta tham chiếu lại **Hình 5.8**, điều này có nghĩa là mẫu nhiễu xạ của một đặc trưng cụ thể sẽ trải ra trên một góc lớn hơn `α`. Điều này ban đầu có vẻ bất lợi, vì nó có nghĩa là một phần thông tin sẽ bị mất do khẩu độ hữu hạn của thấu kính vật kính không thu nhận được. Tuy nhiên, sự trải rộng này cũng có nghĩa là thông tin từ các đặc trưng ở gần nhau — vốn có thể đã hoàn toàn bị mất ra ngoài khẩu độ của thấu kính hội tụ — nay được thu nhận một phần vì nó bị trải rộng vào bên trong khẩu độ thấu kính. Kết quả của các hiệu ứng này là ứng xử của `MTF` theo kích thước đặc trưng được thay đổi như trình bày trong **Hình 5.13**. Khi `s` tăng, nguồn trở nên ít kết hợp hơn, và `MTF` bị suy giảm phần nào đối với các đặc trưng lớn. Tuy nhiên, nó được cải thiện đối với các đặc trưng nhỏ nhất, và đây thường là một đánh đổi tốt trong các hệ tạo ảnh chiếu ảnh đang được đẩy đến giới hạn độ phân giải. Trong thực tế, độ kết hợp không gian từ `0,5` đến `0,7` thường được sử dụng trong sản xuất chip, theo định nghĩa trong Phương trình `5.10b`.

---

**Hình 5.13:** Hàm truyền điều biến (`MTF`) theo kích thước đặc trưng trong ảnh. Khi `s` tăng (nguồn ít kết hợp hơn), `MTF` suy giảm đối với các đặc trưng lớn hơn nhưng cải thiện đối với các đặc trưng rất nhỏ.

---

### 5.2.2.3 Các hệ thống tiếp xúc và tiếp cận — nhiễu xạ Fresnel

Các hệ thống phơi chiếu tiếp xúc (`contact`) và tiếp cận (`proximity`) (**Hình 5.3**) hoạt động trong chế độ nhiễu xạ trường gần hay nhiễu xạ Fresnel. Không có thấu kính nào giữa `mask` và `resist` trên wafer, nên mẫu nhiễu xạ thu được từ ánh sáng đi qua `mask` tác động trực tiếp lên bề mặt `resist`. Do đó, `aerial image` được tạo ra phụ thuộc vào mẫu nhiễu xạ trường gần.

**Hình 5.14** minh họa tình huống này về mặt khái niệm. Chúng ta giả sử tạm thời rằng `mask` và wafer cách nhau một khoảng hở nhỏ `g`. Một sóng phẳng được giả sử chiếu tới một khẩu độ trong `mask`. Mẫu nhiễu xạ ở phía bên kia của `mask` có thể được dựng bằng cách tưởng tượng các sóng con Huygens phát ra từ mỗi điểm trong khẩu độ. Phân bố cường độ ánh sáng thu được tác động lên bề mặt trên của `resist` cũng được minh họa trong **Hình 5.14**. Có một số đặc điểm đáng quan tâm trong phân bố ánh sáng. Thứ nhất, lưu ý rằng cường độ tăng dần ở gần các cạnh của khẩu độ `mask`. Do các hiệu ứng nhiễu xạ, ánh sáng "uốn cong" ra khỏi các cạnh khẩu độ, tạo ra sự phơi `resist` phần nào bên ngoài các cạnh khẩu độ. Thứ hai, lưu ý sự "rung chuông" (`ringing`) trong phân bố cường độ bên trong kích thước khẩu độ. Điều này phát sinh do sự giao thoa tương hỗ xây dựng và hủy diệt giữa các sóng con Huygens phát ra từ khẩu độ. Các máy in tiếp xúc và tiếp cận thường sử dụng nhiều bước sóng để phơi và cũng không dùng các nguồn sáng có độ kết hợp không gian hoàn hảo. Cả hai cách tiếp cận này đều giảm thiểu các hiệu ứng rung chuông minh họa trong **Hình 5.14**, nhưng dĩ nhiên không loại bỏ hoàn toàn các hiệu ứng nhiễu xạ.

Khi khoảng cách `g` giữa `mask` và `resist` tăng lên, chất lượng của `aerial image` tạo ra tại bề mặt `resist` sẽ suy giảm vì các hiệu ứng nhiễu xạ sẽ trở nên quan trọng hơn. Các máy in tiếp xúc giảm thiểu các hiệu ứng này bằng cách cố gắng giảm `g` về không, nhưng trong hầu hết các hệ thống thực tế, `g` không thật sự bằng không vì bề mặt trên của `resist` không hoàn toàn phẳng do địa hình trên bề mặt wafer. Trong giới hạn khi `mask` và wafer được ép tiếp xúc cứng với nhau, độ phân giải của các hệ thống như vậy có thể rất tốt (rõ ràng dưới `0,1 µm`). Tuy nhiên, ngay cả trong trường hợp này, bản thân `resist` vẫn có chiều dày hữu hạn và độ phân giải vẫn bị giới hạn bởi sự tán xạ ánh sáng trong `resist` và sự phản xạ ánh sáng từ các đặc trưng bề mặt trên wafer bên dưới, vốn tán xạ ánh sáng theo chiều ngang vào các vùng lân cận các khẩu độ `mask`. Chúng ta sẽ thảo luận một số vấn đề tán xạ này cẩn thận hơn trong phần tiếp theo về phơi `resist`.

---

**Hình 5.14:** Hệ phơi chiếu tiếp xúc hoặc trường gần cơ bản, minh họa việc sử dụng các sóng con Huygens phát ra từ một khẩu độ trong `mask`. Kích thước đặc trưng trên `mask` được giả sử là `W`, cùng với khoảng cách giữa `mask` và `resist` là `g`. Phân bố cường độ ánh sáng thu được (`aerial image`) tại bề mặt `resist` được trình bày ở bên phải.

---

Nói chung, `aerial image` có thể được tính toán bằng lý thuyết nhiễu xạ Fresnel khi khoảng hở `g` nằm trong các giới hạn

---

> **[Công thức toán]**
>
> $$
> \lambda < g < \frac{W^2}{\lambda}
> \tag{5.11}
> $$

---

trong đó `W` là kích thước của khẩu độ `mask` (kích thước đặc trưng). Giới hạn dưới của `g` chắc chắn được thỏa mãn bởi các hệ thống in tiếp cận và thường cũng được thỏa mãn bởi các hệ thống in tiếp xúc trừ khi sử dụng tiếp xúc cứng. Nếu `g` xuống dưới bước sóng của ánh sáng dùng để phơi, phân bố cường độ ánh sáng thu được vẫn có thể được tính toán nhưng chỉ bằng cách giải số đầy đủ các phương trình Maxwell. Các nghiệm như vậy rất phức tạp, nhưng may mắn thay hiếm khi cần thiết `[5.6]`. Giới hạn trên của `g` xuất hiện vì khi `g` tăng, lý thuyết nhiễu xạ Fresnel phải được thay thế bằng lý thuyết nhiễu xạ trường xa (Fraunhofer) để tính toán `aerial image`.

Trong miền nhiễu xạ Fresnel, kích thước đặc trưng nhỏ nhất có thể phân giải được là vào cỡ

---

> **[Công thức toán]**
>
> $$
> W_{min} \approx \sqrt{\lambda g}
> \tag{5.12}
> $$

---

Do đó, một hệ thống in tiếp cận hoạt động với khoảng hở `10 µm` và nguồn sáng vạch `i` (`λ = 365 nm`), có thể phân giải các đặc trưng hơi nhỏ hơn `2 µm`. Điều này lớn hơn nhiều so với các kích thước sử dụng trong các chip `VLSI` hiện đại, vì vậy các hệ thống này không phù hợp để sản xuất các chip như vậy. Tuy nhiên, các máy in tiếp cận rẻ hơn nhiều so với các hệ thống chiếu ảnh đã mô tả trước đó, nên đối với các ứng dụng mà kích thước đặc trưng tương thích với chúng, máy in tiếp cận là một giải pháp tiết kiệm.

---

**Hình 5.15** cố gắng tóm tắt về mặt khái niệm phần thảo luận trong hai mục trước. Chúng ta tưởng tượng một sóng phẳng đi qua một khẩu độ `mask`. Khẩu độ được tạo ảnh lên `resist` trên một wafer thông qua một trong ba loại hệ thống phơi chiếu. Trong trường hợp in tiếp xúc, một ảnh có độ phân giải rất cao được tạo ra vì `mask` và `resist` được giả sử ở trong tiếp xúc cứng. Nếu wafer và `mask` bị tách nhau một khoảng nhỏ như trong hệ thống in tiếp cận, độ phân giải suy giảm do các hiệu ứng nhiễu xạ Fresnel trường gần. Cuối cùng, nếu chúng ta đặt một thấu kính giữa `mask` và wafer và hội tụ hình ảnh của khẩu độ lên wafer, một ảnh đặc trưng bởi nhiễu xạ Fraunhofer được tạo ra. Trong ví dụ trong hình này, độ phân giải của ảnh từ hệ thống tiếp cận được minh họa là kém hơn cả hai hệ thống còn lại. Đây thường là trường hợp trong các hệ thống thực tế, như chúng ta đã thấy trong ví dụ số ở phần trước, và đó là lý do tại sao các hệ thống chiếu ảnh được sử dụng trong sản xuất ngày nay.

---

**Hình 5.15:** Các `aerial image` được tạo ra bởi ba loại thiết bị quang khắc quang học. `Mask` và wafer sẽ ở trong tiếp xúc cứng trong một máy căn chỉnh tiếp xúc (`contact aligner`), cách nhau một khoảng hở `g` trong một máy căn chỉnh tiếp cận (`proximity aligner`), và ở xa nhau với một thấu kính hội tụ xen giữa trong một hệ thống chiếu ảnh (`projection system`).

---
## 5.2.3 Photoresist

Các vật liệu `photoresist` được thiết kế để phản ứng với các photon tới bằng cách thay đổi tính chất của chúng khi bị phơi với ánh sáng. Dĩ nhiên nhiều vật liệu hấp thụ ánh sáng, nhưng thường sự hấp thụ dẫn đến các quá trình điện tử hơn là các biến đổi hóa học. Ví dụ, các chất bán dẫn hấp thụ photon và năng lượng được truyền cho các electron và lỗ trống. Như chúng ta đã thấy trong các chương trước, các hạt tải tự do sẽ tiêu tán năng lượng hấp thụ thông qua tái hợp hoặc thông qua các tương tác phonon (truyền năng lượng thành nhiệt). Trong một số trường hợp, năng lượng thực sự có thể được thu hoạch như trong các pin mặt trời. Không có quá trình nào trong số này hữu ích trong quang khắc, vì trong `photoresist` chúng ta yêu cầu một vật liệu duy trì một `latent image` (ảnh tiềm ẩn) của các photon tác động ít nhất cho đến khi `resist` được hiện hình. Một phản ứng tồn tại lâu dài với ánh sáng nói chung đòi hỏi một sự thay đổi hóa học trong vật liệu.

Hầu như tất cả các `resist` ngày nay đều được chế tạo từ các vật liệu nền hydrocarbon. Khi các vật liệu này hấp thụ ánh sáng, năng lượng từ các photon nói chung phá vỡ các liên kết hóa học. Sau khi điều này xảy ra, vật liệu `resist` tự tái cấu trúc hóa học thành một dạng ổn định mới. `Resist` dương (`positive resist`) phản ứng với ánh sáng bằng cách trở nên dễ hòa tan hơn trong dung dịch hiện hình (`developer`). `Resist` âm (`negative resist`) thì ngược lại — chúng trở nên kém hòa tan hơn ở những vùng bị phơi. Thực tiễn hiện nay trong ngành công nghiệp bán dẫn chủ yếu dựa vào `resist` dương vì chúng nói chung có độ phân giải tốt hơn so với `resist` âm.

Các `photoresist` đang sử dụng ngày nay là chất lỏng ở nhiệt độ phòng và được phủ lên bề mặt wafer bằng cách đặt chất lỏng lên wafer rồi quay wafer ở vài nghìn `RPM`. Tốc độ quay và độ nhớt của `resist` quyết định chiều dày `resist` cuối cùng, thường `≈ 0,6 - 1 µm`. Độ nhớt của `resist` được kiểm soát bởi dung môi, là một thành phần của `resist`. Một khi `resist` được phủ quay lên wafer, một bước nung (`prebake`) thường được dùng để đuổi dung môi còn lại. `Resist` sau đó được phơi. Hiện hình được thực hiện bằng dung dịch hiện hình lỏng, hoặc bằng cách nhúng wafer vào chất lỏng, bằng cách phun dung dịch hiện hình lên wafer, hoặc phổ biến nhất là bằng cách đặt một "vũng" dung dịch hiện hình lên wafer. Sau khi hiện hình hoàn tất, `resist` thường được nung lại (`postbake`) để làm cứng nó và cải thiện khả năng đóng vai trò làm `mask` khắc hoặc `mask` cấy ion, tùy thuộc vào bước cụ thể trong `process flow`. Cuối cùng, sau quá trình khắc hoặc cấy ion, `resist` được loại bỏ, thường trong plasma oxy, mặc dù việc tẩy bằng hóa chất cũng có thể được sử dụng.

Một số tham số quan trọng xác định tính hữu dụng của một `resist` cụ thể. Độ nhạy (`sensitivity`) là thước đo lượng ánh sáng cần thiết để phơi `resist`. Thường được đo bằng `mJ cm⁻²`, và đối với các `resist` vạch `g` và vạch `i` thường là `100 mJ cm⁻²`. Các `resist` tử ngoại sâu (`DUV`) thế hệ mới hơn thường đạt được độ nhạy `20 - 40 mJ cm⁻²` vì chúng sử dụng khuếch đại hóa học (`chemical amplification`), một quá trình mà chúng ta sẽ mô tả sau. Nói chung, độ nhạy cao là mong muốn vì điều này giảm thời gian phơi của `resist` và do đó cải thiện thông lượng trong quá trình quang khắc. Tuy nhiên, độ nhạy cực cao thường không được mong muốn vì điều đó có xu hướng làm cho vật liệu `resist` không ổn định, làm cho nó rất nhạy với nhiệt độ và cũng có thể tạo ra các vấn đề với sự biến đổi thống kê do nhiễu `shot` (`shot noise`) trong quá trình phơi. Thường thì độ tương phản cao hơn và độ linh hoạt quy trình (`process latitude`) lớn hơn đạt được ở độ nhạy thấp hơn. Tuy nhiên, các `resist` khuếch đại hóa học `DUV` mới đạt được cả độ nhạy cao hơn và độ tương phản cao hơn so với các `resist` vạch `g` và vạch `i` cũ hơn. Vì ánh sáng dùng để phơi `resist` ở một bước sóng cụ thể, điều quan trọng là độ nhạy của `resist` phải được tối ưu hóa cho bước sóng phơi.

Độ phân giải rõ ràng là quan trọng đối với `resist`. Chất lượng của các mẫu `resist` ngày nay nói chung bị giới hạn bởi hệ thống phơi chiếu (`aerial image`) chứ không phải bởi bản thân `resist`. Tuy nhiên, vật liệu `resist` và các bước quy trình (liều phơi, chu kỳ nung và hiện hình) phải được kiểm soát cẩn thận để đạt được độ phân giải bị giới hạn bởi nhiễu xạ trong các ảnh `resist`.

Tham số quan trọng thứ ba liên quan đến chức năng "`resist`" của `photoresist`. Thuật ngữ "`resist`" (chống chịu) mô tả yêu cầu `photoresist` phải chịu được quá trình khắc hoặc cấy ion sau khi mẫu `mask` được chuyển vào `resist`. Các `resist` thực tế cần có độ bền hợp lý đối với các quá trình này. Trong thực tế, điều này có nghĩa là các `resist` phải có khả năng phân giải các đặc trưng nhỏ ngay cả khi `resist` có chiều dày hợp lý.

Các `photoresist` vạch `g` và vạch `i` nói chung bao gồm ba thành phần: một nhựa nền không hoạt tính (`inactive resin`), thường là một hydrocarbon tạo nên nền vật liệu; một hợp chất quang hoạt (`photoactive compound`, `PAC`), cũng là một hydrocarbon; và một dung môi được dùng để điều chỉnh độ nhớt của `resist`. Các `resist` `DUV` thay thế thành phần `PAC` bằng một chất tạo quang axit (`photo-acid generator`, `PAG`), đóng vai trò như một chất khuếch đại hóa học hay xúc tác, và thường bổ sung thêm các thành phần khác để tăng độ ổn định. Hầu hết dung môi trong `resist` bay hơi trong quá trình phủ quay lên wafer và trong các quá trình `prebake` trước khi phơi `resist`, để lại một vật liệu có tỷ lệ xấp xỉ `1:1` giữa nền và thành phần hoạt tính.

---

### 5.2.3.1 Resist vạch g và vạch i

Các `resist` vạch `g` và vạch `i` được sử dụng phổ biến nhất hiện nay là các vật liệu `diazonaphthoquinone` hay `DNQ`. Nhựa nền thường là `novolac`, có cấu trúc được trình bày trong **Hình 5.16**. `Novolac` là một vật liệu polymer bao gồm các vòng hydrocarbon cơ bản với `2` nhóm methyl và `1` nhóm `OH` gắn vào. Cấu trúc vòng cơ bản được trình bày trong hình có thể được lặp lại nhiều lần để tạo thành một vật liệu polymer chuỗi dài. Bản thân `novolac` sẽ dễ dàng hòa tan trong dung dịch hiện hình với tốc độ hòa tan điển hình khoảng `15 nm s⁻¹`.

Các `PAC` trong các `resist` này thường là các `diazoquinone`. Cấu trúc cơ bản của các hợp chất này được trình bày trong **Hình 5.17**. Phần quang hoạt của cấu trúc là phần nằm phía trên `SO₂`. Phần còn lại của phân tử thường được viết tắt như trình bày trong hình. Vai trò của `PAC` là ức chế sự hòa tan của vật liệu `resist` trong dung dịch hiện hình. Các `diazoquinone` không hòa tan trong các dung dịch hiện hình điển hình và chúng làm giảm tốc độ hòa tan tổng thể của `resist` xuống còn khoảng `1 - 2 nm s⁻¹`. Do đó, vật liệu `DNQ` về cơ bản không hòa tan trong dung dịch hiện hình `resist` trước khi được phơi sáng.

---

**Hình 5.16:** Cấu trúc cơ bản của `novolac`, một nhựa đặc được dùng làm vật liệu nền trong các `positive photoresist`.

---

**Hình 5.17:** Cấu trúc cơ bản của `diazoquinone`, một hợp chất quang hoạt thường được sử dụng trong các `positive photoresist`. `R` đại diện cho phần dưới của phân tử.

---

Khi `resist` bị phơi với ánh sáng, các phân tử `diazoquinone` biến đổi hóa học như minh họa trong **Hình 5.18**. Phân tử `N₂` liên kết yếu trong `PAC`, và phần đầu tiên của phản ứng quang hóa liên quan đến ánh sáng phá vỡ liên kết này. Điều này để lại một vị trí carbon có phản ứng mạnh. Cấu trúc `PAC` có thể tự ổn định bằng cách dịch chuyển một nguyên tử carbon ra ngoài vòng với nguyên tử oxy liên kết cộng hóa trị với nó. Điều này được gọi là sự sắp xếp lại Wolff (`Wolff rearrangement`). Phân tử ketene thu được cuối cùng biến đổi thành axit carboxylic (góc dưới bên trái trong **Hình 5.18**) khi có mặt nước. Axit carboxylic bây giờ dễ dàng hòa tan trong một dung dịch hiện hình kiềm (thường là `TMAH — tetramethyl ammonium hydroxide`, `KOH` hoặc `NaOH` hòa tan trong `H₂O`). Vật liệu nhựa nền `novolac` cũng dễ dàng hòa tan trong dung dịch này. Do đó, vật liệu `resist` đã phơi hòa tan với tốc độ `100 - 200 nm s⁻¹`. Các vùng chưa phơi của `resist` về cơ bản không bị ảnh hưởng bởi dung dịch hiện hình, và vì vậy nếu mẫu đã phơi tái tạo chính xác mẫu `mask`, `photoresist` có thể tạo ra một ảnh độ phân giải cao của `mask`.

---

**Hình 5.18:** Quá trình phân hủy xảy ra trong các `diazoquinone` khi bị phơi với ánh sáng.

---

### 5.2.3.2 Resist tử ngoại sâu (DUV)

Các vật liệu `resist` `DNQ` thông thường có hai vấn đề đáng kể khi sử dụng các bước sóng phơi ngắn hơn. Vấn đề thứ nhất là đối với các bước sóng ngắn hơn vạch `i` (`365 nm`), các `resist` này hấp thụ mạnh các photon tới. Do đó bức xạ tới không thể xuyên qua toàn bộ chiều dày của `resist`. Đây là một vấn đề đáng kể ở `248 nm` (`KrF`), là bước sóng hiện đang được sử dụng cho thế hệ `0,25 µm`. Vấn đề thứ hai liên quan đến độ nhạy của `resist`. Một vài năm trước, khi các `resist` phù hợp cho các ứng dụng `DUV` lần đầu tiên được khám phá, nguồn sáng khả thi duy nhất là đèn hồ quang `Hg`. Các nguồn này hoạt động tốt cho các hệ vạch `g` và vạch `i`, nhưng cường độ đầu ra của chúng trong vùng `DUV` thấp hơn nhiều so với ở vạch `i`. Do đó, vào thời điểm đó người ta tin rằng bất kỳ `resist` nào được sử dụng cho các ứng dụng `DUV` cũng sẽ phải có độ nhạy được cải thiện so với các `resist` `DNQ` tiêu chuẩn, để duy trì thông lượng sản xuất. Tất nhiên, bây giờ các nguồn laser excimer sáng đã sẵn có và đáng tin cậy ở `248 nm`, và do đó vấn đề độ nhạy không còn quan trọng như vậy. Kết quả là, các `resist` kiểu `DNQ` hiện đang được xem xét lại với các hợp chất `PAC` được cải biến, hoạt động hiệu quả hơn ở `248 nm`.

Tuy nhiên, các `resist` `DUV` đang được sử dụng ngày nay không phải là các `resist` `DNQ` được cải biến. Chúng dựa trên một hóa học hoàn toàn mới và sử dụng khuếch đại hóa học (`CA resists`) `[5.7 - 5.9]`. Các `resist` `DNQ` tiêu chuẩn đạt hiệu suất lượng tử khoảng `0,3`. Điều này có nghĩa là khoảng `30%` các photon tới tương tác với các phân tử `PAC` và có hiệu quả trong việc phơi `resist`. Do đó, sự cải thiện độ nhạy có thể với các `resist` này tối đa chỉ là hệ số khoảng `3`. Các `resist` `CA` sử dụng một quá trình phơi khác, trong đó các photon tới phản ứng với một phân tử `PAG`, tạo ra một phân tử axit. Các phân tử axit này sau đó đóng vai trò xúc tác trong quá trình nung `resist` tiếp theo (`PEB — post exposure bake`) để thay đổi các tính chất của `resist` ở các vùng đã phơi. Cả phiên bản `resist` dương lẫn `resist` âm đều có thể thực hiện được. Trong trường hợp `resist` dương, `PAG` khởi tạo một phản ứng hóa học làm cho `resist` hòa tan trong dung dịch hiện hình; trong `resist` âm thì ngược lại. Điểm mấu chốt trong cả hai trường hợp là các phản ứng có tính xúc tác; phân tử axit được tái tạo sau mỗi phản ứng hóa học và do đó có thể tham gia vào hàng chục hoặc hàng trăm phản ứng tiếp theo. Do đó, hiệu suất lượng tử tổng thể trong một `resist` `CA` là tích của hiệu suất ban đầu của phản ứng ánh sáng/`PAG`, nhân với số phản ứng tiếp theo được xúc tác. Tích này có thể lớn hơn `1` rất nhiều và chịu trách nhiệm cho sự cải thiện độ nhạy của các `resist` `DUV` so với các `resist` `DNQ` (`20 - 40 mJ cm⁻²` so với `100 mJ cm⁻²`).

Khuếch đại hóa học là một cách tiếp cận mới rất mạnh để tạo ra các `resist`. Vì số lượng các phản ứng được xúc tác bởi axit có thể lớn hơn nhiều so với số phản ứng quang hóa, một bùng nổ các khả năng `resist` mới đã xảy ra trong những năm gần đây. **Hình 5.19** minh họa nguyên lý cơ bản đằng sau các `resist` này.

---

**Hình 5.19:** Hoạt động cơ bản của một `resist` khuếch đại hóa học (`CA`). `PAG` là chất tạo quang axit; `INSOL` và `SOL` là các phần không hòa tan và hòa tan của polymer nền. Các bước c) và d) có thể lặp lại hàng chục hoặc hàng trăm lần trong quá trình `PEB`.

---

Các `resist` dương bao gồm một `PAG` và một polymer bị chặn hay được bảo vệ (`blocked or protected polymer`), không hòa tan trong dung dịch hiện hình do các phân tử gắn kèm (ký hiệu là `INSOL` trong **Hình 5.19**). Một ví dụ điển hình sẽ là một polymer `polyhydroxystyrene` với các nhóm bất ổn với axit (`acid labile groups`) gắn kèm `[5.10, 5.11]`. Các photon `DUV` tới phản ứng với các phân tử `PAG` để tạo ra một phân tử axit. Do đó, mẫu không gian của các phân tử axit trong `resist` sau khi phơi là một `latent image` axit `3D` "được lưu trữ" của mẫu `mask`. Sau khi phơi, wafer được nung ở nhiệt độ khoảng `120°C` trong vài phút (`post exposure bake` hay `PEB`). Nhiệt cung cấp năng lượng cần thiết cho phản ứng giữa các phân tử axit và các mảnh không hòa tan trên các chuỗi polymer xảy ra. Nó cũng cung cấp tính linh động (thông qua khuếch tán) cho các phân tử axit để tìm các mảnh không hòa tan và phản ứng với hàng chục hoặc hàng trăm mảnh như vậy trong quá trình `PEB`. Do đó, trong quá trình `PEB`, polymer bị chặn không hòa tan được chuyển đổi thành một polymer đã được bỏ chặn (`unblocked polymer`) hòa tan trong dung dịch hiện hình kiềm nước. Trong các `resist` `DUV` hoạt động âm (`negative working`), `PAG` xúc tác một phản ứng tạo ra liên kết ngang (`crosslink`) các chuỗi polymer, làm cho `resist` không hòa tan trong dung dịch hiện hình. Cơ chế then chốt trong cả hai quá trình là hành vi xúc tác của các phân tử axit được tái tạo sau mỗi phản ứng.

Mặc dù các `resist` mới này cung cấp độ nhạy tuyệt vời và độ phân giải hơn đủ cho các cấu trúc linh kiện ngày nay, chúng cũng đòi hỏi kiểm soát chế tạo rất cẩn thận. Vì có một khoảng trễ thời gian giữa việc phơi ánh sáng và phản ứng axit với các mảnh chuỗi polymer, sự đầu độc (`poisoning`) — tức sự nhiễm bẩn — của các phân tử axit là một mối lo ngại. Một số `resist` `DUV` sớm rất nhạy với các nồng độ rất nhỏ của các chất nhiễm bẩn trong không khí, vốn phản ứng với các phân tử axit trước khi chúng có thể xúc tác các phản ứng `resist` trong quá trình `PEB`. Điều này dẫn đến một lớp bề mặt trên `resist` nơi axit bị trung hòa và `resist` thực sự không được phơi. Các loại vấn đề này phần lớn đã được giải quyết bằng cách thêm các thành phần bổ sung vào `resist` `DUV`, bằng cách thêm các lớp bề mặt bảo vệ, và bằng cách kiểm soát môi trường và chế tạo cẩn thận. Các `resist` `DUV` cũng đòi hỏi kiểm soát rất cẩn thận các điều kiện `PEB` vì quá trình nung đó được dùng để thúc đẩy phản ứng hóa học hoàn tất việc phơi `resist`. Các phản ứng hóa học và sự khuếch tán gắn với các phân tử axit trong quá trình `PEB` nói chung phụ thuộc theo hàm mũ vào nhiệt độ, đòi hỏi kiểm soát nhiệt độ ở mức vài phần mười độ `°C` trong quá trình `PEB`.

### 5.2.3.3 Các tính chất cơ bản và đặc trưng hóa của resist

Hai tham số cơ bản thường được dùng để mô tả các tính chất của `photoresist` là độ tương phản (`contrast`) và hàm truyền điều biến tới hạn (`critical modulation transfer function`, `CMTF`). Chúng ta sẽ định nghĩa các thuật ngữ này và giải thích tầm quan trọng của chúng trong các đoạn tiếp theo. Độ tương phản thực chất là thước đo khả năng của `resist` trong việc phân biệt vùng sáng và vùng tối trong `aerial image` mà hệ thống phơi chiếu tạo ra. Như chúng ta đã thấy, các hiệu ứng nhiễu xạ và có thể các sự không hoàn hảo khác trong hệ thống phơi chiếu dẫn đến một `aerial image` không có sự chuyển tiếp đột ngột từ tối sang sáng. Một câu hỏi quan trọng là `resist` phản ứng như thế nào với vùng "xám" ở các cạnh của các đặc trưng trong `aerial image`.

Độ tương phản là một tham số được xác định thực nghiệm cho mỗi `resist` và giá trị của nó được trích xuất từ các đồ thị như trình bày trong **Hình 5.20**. Dữ liệu để xây dựng các đồ thị này được thu được bằng cách phơi các lớp `resist` với nhiều liều phơi khác nhau. Mỗi mẫu sau đó được hiện hình trong một khoảng thời gian cố định và chiều dày của `photoresist` còn lại sau khi hiện hình được đo. Đối với `resist` dương, các mẫu nhận liều phơi nhỏ sẽ không bị tấn công đáng kể bởi dung dịch hiện hình; những mẫu nhận liều lớn sẽ hòa tan hoàn toàn trong dung dịch hiện hình. Các liều trung gian sẽ dẫn đến sự hòa tan một phần của `resist`. Đối với `resist` âm, ứng xử ngược lại xảy ra. Với dữ liệu như trình bày trong hình, độ tương phản đơn giản là độ dốc của phần dốc của đường cong, được định nghĩa là

---

> **[Công thức toán]**
>
> $$
> \gamma = \frac{1}{\log_{10}\!\left(\dfrac{Q_f}{Q_0}\right)}
> \tag{5.13}
> $$

---

trong đó `Q₀` là liều tại đó sự phơi bắt đầu có tác dụng và `Qf` là liều tại đó sự phơi hoàn tất.

---

**Hình 5.20:** Các đường cong độ tương phản lý tưởng hóa cho `resist` dương và `resist` âm.

---

Các `resist` vạch `g` và vạch `i` điển hình đạt được độ tương phản `γ` từ `2 - 3` và giá trị `Qf` khoảng `100 mJ cm⁻²`. Các `resist` `DUV` đạt được độ tương phản tốt hơn đáng kể và độ nhạy tốt hơn so với này. Về cơ bản, điều này là vì sự khuếch đại hóa học xảy ra trong các `resist` `DUV` làm dốc hơn sự chuyển tiếp từ trạng thái chưa phơi sang trạng thái đã phơi. (Một khi phản ứng được bắt đầu, bản chất xúc tác của quá trình dẫn nó đến hoàn tất, không giống như các `resist` `DNQ` nơi mà các phân tử `PAC` trong `resist` phải được phơi từng phân tử một bởi các photon tới trong quá trình phơi.) Do đó, các `resist` `DUV` điển hình đạt được giá trị `γ` từ `5 - 10` và giá trị `Qf` khoảng `20 - 40 mJ cm⁻²`.

Tuy nhiên, điều quan trọng cần lưu ý là `γ` không phải là một hằng số đối với một thành phần `resist` cụ thể. Đúng hơn, giá trị `γ` được trích xuất thực nghiệm phụ thuộc vào các tham số quy trình như hóa học hiện hình, thời gian và nhiệt độ nung trước và sau khi phơi, bước sóng của ánh sáng phơi và cấu trúc bên dưới của wafer mà `resist` được phủ quay lên. Nói chung, điều mong muốn là có một `resist` với độ tương phản cao vì điều này tạo ra các biên dạng cạnh (`edge profiles`) tốt hơn (dốc hơn) trong các mẫu `resist` sau khi hiện hình. (Xem **Hình 5.21**.) Theo trực giác, điều này phát sinh vì độ tương phản cao hàm ý rằng `resist` phân biệt sắc nét giữa vùng tối và vùng sáng trong `aerial image`. Do đó, các `resist` có độ tương phản cao thực sự có thể "làm sắc nét" một `aerial image` kém chất lượng.

---

**Hình 5.21:** Ví dụ về cách chất lượng của `aerial image` và độ tương phản của `resist` kết hợp để tạo ra biên dạng cạnh của `resist`. Bên trái trình bày một `aerial image` sắc nét và các cạnh `resist` dốc (vùng xám). Ví dụ bên phải trình bày một `aerial image` kém hơn và các cạnh dần dần thu được trên biên dạng `resist`.

---

Hàm truyền điều biến (`MTF`) của `aerial image` đã được định nghĩa trong Phương trình `5.9` và trong **Hình 5.10**. `MTF` đơn giản là thước đo cường độ "tối" so với "sáng" trong `aerial image` được tạo bởi hệ thống phơi chiếu. Thường hữu ích khi định nghĩa một đại lượng tương tự cho `resist`, trong trường hợp này gọi là `MTF` tới hạn hay `CMTF`. `CMTF` xấp xỉ là hàm truyền quang học tối thiểu cần thiết để phân giải một mẫu trong `resist`.

---

> **[Công thức toán]**
>
> $$
> CMTF_{\text{resist}}
> = \frac{Q_f - Q_0}{Q_f + Q_0}
> = \frac{10^{1/\gamma} - 1}{10^{1/\gamma} + 1}
> \tag{5.14}
> $$

---

Các giá trị `CMTF` điển hình của các `resist` vạch `g` và vạch `i` vào khoảng `0,4`. Với các giá trị `γ` cao hơn, các `resist` `DUV` khuếch đại hóa học đạt được các giá trị `CMTF` nhỏ hơn đáng kể (`≈ 0,1 - 0,2`). Ý nghĩa của con số này là `CMTF` phải nhỏ hơn `MTF` của `aerial image` thì `resist` mới có thể phân giải được `aerial image`.

Cho đến điểm này trong thảo luận về `resist` của chúng ta, chúng ta thực sự đã xem `resist` như có chiều dày đồng đều và chúng ta cũng đã xem quá trình phơi như xảy ra đồng thời xuyên suốt thể tích của vật liệu `resist`. Trên thực tế, không cái nào trong số này là một giả thiết tốt trong nhiều trường hợp. **Hình 5.22** minh họa một số vấn đề này. Lưu ý trong hình đó rằng chiều dày `resist` có xu hướng không đồng đều trên wafer vì nó được phủ quay dưới dạng chất lỏng và do đó có xu hướng lấp đầy các "đỉnh và thung lũng" của địa hình bên dưới. Do đó, quá trình phơi thường phải đối mặt với việc phơi các vùng khác nhau với các chiều dày `resist` khác nhau. Thực chất, `resist` mỏng hơn ở phía trên các cấu trúc cao và dày hơn ở phía trên các cấu trúc thấp. Điều này có thể là một vấn đề đặc biệt ở các cạnh của các màng mỏng bên dưới, nơi chiều dày `resist` có thể thay đổi đột ngột. Kết quả của các hiệu ứng này là `resist` có thể bị phơi thiếu ở những nơi dày hơn và phơi thừa ở những nơi mỏng hơn. Điều này có thể dẫn đến sự biến thiên chiều rộng vạch (`linewidth`), đặc biệt ở nơi các đặc trưng `photoresist` vượt qua các bậc trong các cấu trúc bên dưới.

---

**Hình 5.22:** Quá trình phơi gắn với các Hình `2.36` và `2.37` trong `process flow` `CMOS` ở Chương `2`. Các thanh đen trong `aerial image` biểu diễn các vùng trên `mask` là bất trong suốt và do đó lý tưởng là không có photon nào tác động lên `resist` ở các vùng đó.

---

Vấn đề thứ hai là sự hấp thụ ánh sáng bởi `resist` biến thiên theo độ sâu bên dưới bề mặt `resist` và nó cũng thay đổi theo thời gian trong quá trình phơi. Lại tưởng tượng trong mối liên hệ với **Hình 5.22** rằng quá trình phơi vừa bắt đầu. Nồng độ `PAC` được giả sử đồng đều xuyên suốt `resist`. Khi các phân tử `PAC` gần bề mặt `resist` hấp thụ các photon ánh sáng, các photon đó không còn sẵn có để phơi các lớp sâu hơn của `resist`. Do đó, nồng độ ánh sáng giảm dần theo độ sâu. Chúng ta sẽ mô hình hóa điều này cẩn thận hơn trong Mục `5.5`, nhưng ở bậc thứ nhất, cường độ ánh sáng giảm theo hàm mũ với khoảng cách vào trong `resist`.

---

> **[Công thức toán]**
>
> $$
> I = I_0\, e^{-\alpha z}
> \tag{5.15}
> $$

---

trong đó `z` là độ sâu bên dưới bề mặt, `I₀` là cường độ tại bề mặt và `α` là hệ số hấp thụ quang học trong `resist`. Do đó, `resist` được phơi trước tiên ở gần bề mặt trên.

May mắn thay, một quá trình được gọi là "tẩy trắng" (`bleaching`) xảy ra trong các `resist` `DNQ` vạch `g` và vạch `i`. Khi `resist` được phơi, `PAC` bị biến đổi, hấp thụ ngày càng ít ánh sáng hơn, và do đó nó trở nên ngày càng trong suốt hơn. Do đó, khi các lớp trên cùng của `resist` được phơi, chúng truyền nhiều ánh sáng hơn tới các lớp sâu hơn, vốn được phơi tiếp theo. Điều này dẫn đến sự phơi đồng đều hơn. Quá trình tẩy trắng không có gì đáng ngạc nhiên vì khi thành phần `PAC` của các `resist` này phản ứng và chuyển đổi thành axit carboxylic, nhiều ánh sáng hơn sẽ đi qua tới các lớp sâu hơn. Việc mô hình hóa chi tiết các hiệu ứng này cũng phải bao gồm sự hấp thụ ánh sáng bởi thành phần nền `novolac` của `resist`, như chúng ta sẽ thấy trong Mục `5.5`. Tẩy trắng thường không xảy ra trong các `resist` `DUV`. Đây là một vấn đề với các vật liệu này vì ánh sáng có thể phản xạ từ các bề mặt bên dưới `resist` trong suốt toàn bộ quá trình phơi. Vấn đề này có thể được giảm thiểu bằng cách sử dụng các lớp phủ chống phản xạ bên dưới `resist` `DUV` (xem phần dưới) và các chất màu (`dyes`) trong bản thân `resist` để giảm thiểu sự phản xạ.

Nếu có các lớp phản xạ cao bên dưới `photoresist`, ánh sáng đi qua toàn bộ `resist` mà không bị hấp thụ sẽ bị phản xạ bởi các lớp bên dưới này và đi ngược trở lên xuyên qua `resist` lần nữa. Mặc dù điều này có thể tăng tốc quá trình phơi, nó cũng có tiềm năng tạo ra các mẫu sóng dừng (`standing wave`) ánh sáng trong `resist` do sự giao thoa tương hỗ xây dựng và hủy diệt giữa các sóng tới và sóng phản xạ. Hơn nữa, nếu ánh sáng bị tán xạ theo chiều ngang, độ phân giải ảnh có thể bị suy giảm. **Các Hình 5.23** và **5.24** minh họa các vấn đề này.

---

**Hình 5.23:** Quá trình phơi quang khắc xảy ra giữa các Hình `2.39` và `2.40` trong `process flow` `CMOS` được mô tả ở Chương `2`. Các ký hiệu `A` và `B` chỉ ra các ví dụ về các mẫu sóng dừng và sự tán xạ ánh sáng theo chiều ngang tương ứng.

---

Trong một số trường hợp, một lớp phủ chống phản xạ (`ARC — antireflective coating`) được lắng đọng lên wafer trước khi phủ quay `resist`. Điều này có thể giúp ích rất nhiều trong việc giảm thiểu các hiệu ứng sóng dừng, nhưng dĩ nhiên làm tăng độ phức tạp của quy trình. Một cách tiếp cận khác thường được sử dụng trong các `resist` vạch `g` và vạch `i` là thêm các chất màu vào `resist`, các chất này hấp thụ ánh sáng và giảm thiểu sự phản xạ.

Các "cạnh có hình răng cưa" (`scalloped edges`) minh họa trong **Hình 5.24** cũng bị ảnh hưởng mạnh bởi việc nung `resist` sau khi phơi nhưng trước khi hiện hình, vì quá trình xử lý nhiệt này cho phép sự khuếch tán của `PAC` trong các `resist` vạch `g` và vạch `i`, hoặc của `PAG` trong các `resist` `DUV`, ở mức độ hạn chế. Điều này làm mịn mẫu sóng dừng. Hoàn toàn có thể mô hình hóa các hiệu ứng sóng dừng này và dự đoán các mẫu cạnh `resist` thu được. Chúng ta sẽ xem xét các vấn đề này cẩn thận hơn trong Mục `5.5`.

---

**Hình 5.24:** Mẫu cường độ ánh sáng thu được từ một sóng dừng được phác thảo ở bên trái. Một ảnh `photoresist` minh họa các hiệu ứng này sau khi hiện hình được trình bày ở bên phải, do A. Vladar và P. Rissman, Hewlett Packard cung cấp.

---

## 5.2.4 Kỹ thuật thiết kế mask — Hiệu chỉnh lân cận quang học và dịch pha

Trong phần thảo luận của chúng ta cho đến điểm này, chúng ta đã xem `mask` đơn giản như một thiết bị số nhị phân. Tức là, nó có các vùng trong suốt và vùng tối, và các mẫu của các vùng này biểu diễn chính xác mẫu mà chúng ta muốn in vào `resist` trên wafer. Thực ra, có thể làm tốt hơn điều này trong việc thiết kế `mask` nếu mục tiêu là tạo ra `aerial image` chất lượng cao nhất. Chúng ta sẽ thảo luận ngắn gọn hai cách tiếp cận để làm điều này — hiệu chỉnh lân cận quang học (`optical proximity correction`, `OPC`) và `mask` dịch pha (`phase shift mask`, `PSM`). Các cách tiếp cận này có thể được xem là "kỹ thuật thiết kế `mask`". Các phương pháp này đôi khi cũng được gọi là "kỹ thuật mặt sóng" (`wavefront engineering`) `[5.12]`.

Chúng ta đã thấy trong phần thảo luận về các hệ thống phơi chiếu rằng khẩu độ hữu hạn của các hệ thống chiếu ảnh dẫn đến sự mất mát của một phần ánh sáng bị nhiễu xạ từ các đặc trưng `mask`. Ngoài kích thước hữu hạn của chúng, các khẩu độ và thấu kính trong các hệ thống chiếu ảnh nói chung là tròn, không phải vuông hay chữ nhật như hầu hết các đặc trưng trên `mask`. Những gì bị mất là các thành phần tần số cao của mẫu nhiễu xạ. Thông tin bị mất này dẫn đến một `aerial image` có các góc bo tròn thay vì vuông, sự thay đổi chiều rộng vạch giữa các vạch cô lập và các vạch nhóm, và sự rút ngắn các đầu của các đặc trưng tuyến tính hẹp. Các hiệu ứng này hoàn toàn có thể dự đoán được và về nguyên tắc có thể được bù phần nào bằng cách điều chỉnh các kích thước và hình dạng đặc trưng trên `mask`. Về nguyên tắc, điều này có thể được thực hiện hoàn toàn thông qua phần mềm một khi thiết kế `mask` hoàn tất. Vấn đề rất khó trong trường hợp tổng quát vì độ phức tạp của các `mask` hiện đại. Một ví dụ về những gì có thể đạt được được trình bày trong **Hình 5.25** `[5.13]`.

**Hình 5.25:** Các mẫu `mask` không có (trái) và có (phải) `OPC` được trình bày ở trên. Các `aerial image` tương ứng (được tính toán) được trình bày ở dưới. Lưu ý sự cải thiện về chất lượng của `aerial image` khi sử dụng `OPC`. Các đường tối trong các mẫu ở dưới chỉ ra sự khác biệt giữa `mask` và `aerial image` trong mỗi trường hợp `[5.13]`. In lại với sự cho phép của `SPIE`.

---

Một cách tiếp cận thứ hai trong kỹ thuật thiết kế `mask` liên quan đến việc thực sự thay đổi các đặc tính truyền qua của `mask` ở các vùng chọn lọc. Năm `1982`, Levenson và cộng sự đề xuất sử dụng các kỹ thuật dịch pha để cải thiện độ phân giải của `aerial image` được in `[5.14]`. Một ví dụ đơn giản về nguyên lý được minh họa trong **Hình 5.26**. Trong ví dụ này, một `mask` tuần hoàn với các vạch và khe bằng nhau (cách tử nhiễu xạ) được dùng làm `mask`. Bên trái trình bày điện trường `ε` gắn với ánh sáng ngay sau khi nó đi qua `mask` và cũng tại wafer (mẫu nhiễu xạ trường xa), không có bất kỳ sự dịch pha nào trong `mask`. Chu kỳ của cách tử được chọn trong trường hợp này sao cho các vạch trên `mask` vừa đủ được phân giải trên wafer. `Photoresist` phản ứng với cường độ ánh sáng, tức bình phương điện trường `ε²`, và do đó mẫu cường độ ở dưới bên trái vừa đủ để phân giải hai vạch.

Trong ví dụ ở bên phải, một vật liệu có chiều dày và chiết suất được chọn để dịch pha ánh sáng đúng `180°` được thêm vào `mask`. Chiều dày của lớp này được cho bởi

---

> **[Công thức toán]**
>
> $$
> d = \frac{\lambda}{2(n-1)}
> \tag{5.16}
> $$

---

trong đó `n` là chiết suất của vật liệu dịch pha. Chu kỳ của mẫu được thêm vào này bằng một nửa chu kỳ của cách tử ban đầu. Các điện trường tương ứng tại `mask` và wafer cũng được trình bày. Vì cường độ ánh sáng tại `aerial image` là bình phương của cường độ điện trường, chất lượng của `aerial image` thu được được cải thiện đáng kể như minh họa. Các kỹ thuật dịch pha như vậy có thể được sử dụng để cải thiện chất lượng của `aerial image` hoặc để cải thiện độ sâu tiêu cự của hệ thống phơi chiếu ở độ phân giải không đổi bằng cách sử dụng hệ thống `NA` thấp hơn.

---

**Hình 5.26:** Ví dụ về việc sử dụng các kỹ thuật dịch pha trên `mask` để cải thiện độ phân giải của `aerial image`. Theo Levenson và cộng sự `[5.32]`.

---

Việc áp dụng nguyên lý này cho các hình dạng `mask` tùy ý khá phức tạp và nói chung đòi hỏi phải thêm các đặc trưng trên `mask` nhỏ hơn kích thước đặc trưng tối thiểu cần in. Các công cụ mô phỏng cung cấp một cách tiếp cận rất mạnh để khảo sát các lợi ích của các `phase shift mask` và chúng cũng có thể giúp ích trong việc thiết kế tối ưu các mẫu `mask`. Chúng ta sẽ xem xét một ví dụ ở phần sau trong Mục `5.5`.

Một điểm cuối cùng liên quan đến các `mask` đáng được đề cập. Chúng ta đã giả sử trong thảo luận của mình rằng một `mask` số nhị phân đơn giản (không có `OPC` hay dịch pha) là một bản sao chính xác của mẫu mong muốn được thiết kế trong hệ thống `CAD`. Khi các kích thước hình học ngày càng nhỏ hơn, điều này càng kém đúng hơn vì chính các hệ thống chế tạo `mask` cũng có các giới hạn độ phân giải. Ngay cả ở tỷ lệ `4X` hoặc `5X` so với các mẫu trên wafer, các mẫu `mask` có thể có các góc bo tròn hoặc các "sự không hoàn hảo" khác làm suy giảm chất lượng của `aerial image` được tạo ra trên wafer.

---

## 5.3 Các phương pháp và thiết bị sản xuất

Quá trình quang khắc chi phối chi phí và thông lượng của công nghệ chế tạo `IC` hiện đại. Vì `SIA NTRS` được thúc đẩy bởi sự giảm liên tục về chiều rộng vạch, quang khắc được kỳ vọng sẽ duy trì vị trí then chốt này trong tương lai. Trong phần này, chúng ta sẽ khảo sát các quy trình và thiết bị công nghiệp điển hình cho quang khắc. Mặc dù các máy in tiếp xúc và tiếp cận đóng vai trò quan trọng trong những ngày đầu của ngành công nghiệp silicon, chúng không còn như vậy nữa vì các mức độ khuyết tật không chấp nhận được và/hoặc độ phân giải hạn chế. Do đó, chúng ta sẽ giới hạn thảo luận trong phần này cho các máy căn chỉnh chiếu ảnh (`projection aligners`). Ngoài ra, vì các `resist` dương `DNQ` và các `resist` `DUV` cho hệ thống `248 nm` chi phối sử dụng công nghiệp ngày nay, chúng ta sẽ giới hạn thảo luận của mình cho các vật liệu này.

---

### 5.3.1 Các hệ thống phơi chiếu wafer

Các máy căn chỉnh chiếu ảnh (`projection aligners`) đã là các thiết bị phơi chiếu chi phối trong ngành công nghiệp silicon trong hơn `20` năm. Tập đoàn `Perkin-Elmer` đã tiên phong trong các hệ thống sớm nhất loại này với tên gọi `Micralign`. Các hệ thống này là các máy căn chỉnh chiếu ảnh kiểu quét (`scanning projection aligners`), sử dụng các `mask` tỷ lệ `1:1`. Nguyên lý đằng sau các hệ thống quét như vậy được minh họa trong **Hình 5.27**. Ý tưởng cơ bản trong các hệ thống này là việc hiệu chỉnh quang học để khắc phục sai lệch (`aberrations`) trong một vùng nhỏ dễ hơn so với trong một vùng lớn. Do đó, nguồn chiếu sáng tạo ra một khe sáng được quét cơ học qua `mask`. Wafer được quét đồng thời sao cho mẫu `mask` được in qua wafer. Hệ thống được minh họa trong **Hình 5.27** là một hệ thống thuần phản xạ, sử dụng các gương. Các hệ thống loại tổng quát này cũng được sử dụng có kết hợp cả gương lẫn thấu kính (cả quang học phản xạ lẫn khúc xạ). Các hệ quang học như vậy được gọi là các hệ quang học `catadioptic`.

Mặc dù các hệ thống quét loại minh họa trong **Hình 5.27** rất tiết kiệm chi phí và có thông lượng cao, chúng yêu cầu các `mask` `1X` chứa thông tin mẫu cho tất cả các chip cần in trên mỗi wafer. Việc kiểm soát chiều rộng vạch trên các `mask` như vậy trở nên khó khăn hơn khi kích thước hình học thu nhỏ. Ngoài ra, khi các chip trở nên phức tạp hơn và khi wafer ngày càng lớn hơn vào cuối những năm `1970`, việc chế tạo các `mask` wafer đầy đủ hoàn hảo và tạo ra các hệ quang học có thể quét toàn bộ wafer với độ phân giải yêu cầu ngày càng trở nên khó khăn. Các hệ thống quét nói chung cũng chỉ cho phép căn chỉnh tổng thể (`global alignment`) của `mask` và các mẫu wafer, tức là căn chỉnh ở mức wafer trước khi quét bắt đầu. Với các kích thước chặt hơn và nhu cầu tương ứng về độ chính xác đặt vị trí tốt hơn, việc căn chỉnh cục bộ theo từng die hoặc trên một tỷ lệ tương tự thường rất được mong muốn. Giải pháp cho các vấn đề này là thay thế các hệ thống quét bằng các `stepper` chỉ phơi một phần hạn chế của wafer (thường là vài `cm²`) tại một thời điểm. Điều này loại bỏ kích thước wafer như một vấn đề chính. Vấn đề `mask` cũng được giải quyết trong các hệ thống này bằng cách làm cho các `stepper` thu nhỏ ảnh đi `4X` hoặc `5X`. Do đó các `mask` sử dụng các kích thước lớn hơn nhiều, làm cho chúng dễ sửa chữa hơn và chúng chỉ chứa một vài die thay vì mẫu wafer đầy đủ. Các `stepper` cũng cho phép căn chỉnh theo từng trường phơi và do đó cải thiện độ chính xác `overlay` so với các máy quét wafer đầy đủ. (Tuy nhiên, khả năng này không thường được sử dụng trong sản xuất vì các vấn đề thông lượng.) Các máy căn chỉnh chiếu ảnh `"step and repeat"` như vậy đã chi phối ngành công nghiệp trong thập kỷ qua. Hầu hết, các hệ thống này sử dụng các hệ quang học thuần khúc xạ (`purely refractive`). Về mặt khái niệm, chúng rất giống hệ thống trình bày trong **Hình 5.3**.

Mặc dù chúng ta đã mô tả các đặc trưng cơ bản và hiệu năng của các `stepper` chiếu ảnh này ở phần trước trong chương này, có một số ý tưởng bổ sung quan trọng được sử dụng trong thực tế để cải thiện hiệu năng của các hệ thống này. Bao gồm việc sử dụng chiếu sáng Kohler (`Kohler illumination`) và chiếu sáng lệch trục (`off-axis illumination`), mà chúng ta sẽ mô tả ngắn gọn ở đây.

**Hình 5.28** minh họa ý tưởng đằng sau một nguồn chiếu sáng Kohler. Ánh sáng đi qua `mask` được hội tụ tại `entrance pupil` (đồng tử vào) của thấu kính chiếu ảnh, thay vì có ánh sáng chuẩn trực đi qua `mask` như minh họa về mặt khái niệm trong **Hình 5.3**. Lý do sử dụng cách bố trí nguồn Kohler là để thấu kính chiếu ảnh có thể thu nhận ánh sáng bị nhiễu xạ từ bất kỳ đặc trưng nào trên `mask` một cách đồng đều như nhau. Điều này được minh họa trong **Hình 5.28** bởi các tam giác phát ra từ các khẩu độ `mask` đại diện cho sự trải rộng góc của ánh sáng bị nhiễu xạ. Nếu sử dụng ánh sáng chuẩn trực qua `mask`, rõ ràng là phần lớn ánh sáng bị nhiễu xạ sẽ bị mất từ các đặc trưng `mask` ở gần cạnh ngoài của `mask`.

---

**Hình 5.27:** Sơ đồ khái niệm của một máy in chiếu ảnh kiểu quét.

---

**Hình 5.28:** Hệ chiếu sáng Kohler. Các tam giác phát ra từ các vùng `mask` đại diện cho mẫu ánh sáng bị nhiễu xạ.

---

"Thủ thuật" thứ hai thường được sử dụng trong các máy căn chỉnh chiếu ảnh hiện đại là chiếu sáng lệch trục (`off-axis illumination`). Ý tưởng đằng sau kỹ thuật này có thể được hiểu trong mối liên hệ với **Hình 5.29**. Nếu ánh sáng từ một nguồn kết hợp chiếu tới `mask` ở một góc so với `mask`, thay vì vuông góc với `mask`, chiếu sáng này được gọi là chiếu sáng lệch trục. Chiếu sáng như vậy rõ ràng thay đổi góc của ánh sáng đi qua `mask`, và cũng thay đổi góc của ánh sáng bị nhiễu xạ. Mặc dù một phần ánh sáng bị nhiễu xạ sẽ bị mất khi sử dụng chiếu sáng lệch trục vì nó sẽ nằm ngoài khẩu độ thấu kính chiếu ảnh, một phần ánh sáng bị nhiễu xạ bậc cao hơn vốn sẽ bị mất khi dùng bức xạ chiếu thẳng góc cũng sẽ được thu nhận trong hệ thống lệch trục. Kết quả cuối cùng là độ phân giải có thể được cải thiện phần nào. Ý tưởng cơ bản tương tự như các lập luận đã trình bày trước đó về việc sử dụng chiếu sáng kết hợp một phần thay vì chiếu sáng kết hợp hoàn toàn. Do đó rõ ràng là cần phải dành sự chú ý đáng kể cho phần chiếu sáng của hệ quang học khi hiệu năng của các máy căn chỉnh chiếu ảnh được đẩy tới các giới hạn vật lý.

---

**Hình 5.29:** Minh họa ý tưởng về chiếu sáng trên trục (`on-axis illumination`) (trên) và chiếu sáng lệch trục (`off-axis illumination`) (dưới). Các vùng tô bóng phát ra từ các vùng `mask` đại diện cho mẫu ánh sáng bị nhiễu xạ. Các triển khai thực tế nói chung sử dụng một nguồn sáng tạo ra nhiều góc chiếu sáng khác nhau (`+` và `-`). Một phần thông tin nhiễu xạ bậc cao hơn được thu nhận trong hệ thống lệch trục.

---

Trong vài năm gần đây, việc chế tạo các `stepper` có cả độ phân giải theo yêu cầu của `SIA NTRS` lẫn trường nhìn theo yêu cầu của lộ trình này ngày càng trở nên khó khăn hơn. Vì lý do này, một loại hệ thống lai kết hợp cả bước (`stepping`) lẫn quét (`scanning`) gần đây đã được đưa vào sử dụng. **Hình 5.30** minh họa nguyên lý. Bước (`stepping`) được dùng để di chuyển wafer giữa các trường phơi chính. Trong mỗi trường phơi, mẫu `mask` được quét qua wafer. Loại hệ thống này có một số ưu điểm của các máy quét (hệ quang học chỉ cần "hoàn hảo" trong một vùng nhỏ hơn). Nó cũng có một số ưu điểm của các hệ thống `stepper` (có thể sử dụng thu nhỏ `4X` hoặc `5X` để đơn giản hóa việc chế tạo `mask`, và tổng trường được in tại mỗi lần phơi nhỏ hơn nhiều so với wafer, loại bỏ kích thước wafer như một vấn đề chính và đơn giản hóa thiết kế thấu kính). Tuy nhiên, hệ cơ khí cần phải quét `mask` nhanh hơn wafer `4X` hoặc `5X` lần và giữ chúng đồng bộ. Các hệ thống lai này cũng cho phép căn chỉnh cục bộ của mẫu `mask` với wafer tại mỗi trường phơi, đây là một trong những ưu điểm vốn có của các hệ thống `stepper`. Tuy nhiên, các hệ thống này rất phức tạp và rất đắt tiền vì chúng có một số nhược điểm của mỗi loại hệ thống (chuyển động cơ học đồng bộ của các máy quét, và thiết kế thấu kính khúc xạ tốn kém của các `stepper`). Tuy nhiên, có khả năng các hệ thống lai này sẽ được sử dụng rộng rãi qua vài thế hệ công nghệ tiếp theo.

---

**Hình 5.30:** Hệ thống `step and scan`. Bước (`stepping`) thực hiện các di chuyển chính từ trường phơi này sang trường phơi khác. Trong mỗi trường phơi, mẫu `mask` được quét qua trường.

---

### 5.3.2 Photoresist

Các chi tiết thực tế gắn với việc phơi và xử lý `photoresist`, không ngạc nhiên, phức tạp hơn đáng kể so với những gì mô tả định tính đưa ra trước đó có thể gợi ý. Các chi tiết bổ sung mà chúng ta sẽ xem xét ở đây nói chung được thiết kế để làm cho toàn bộ quy trình có thể chế tạo được tốt hơn. **Hình 5.31** minh họa một `process flow` điển hình gắn với quang khắc. Các con số cụ thể đề cập đến các điều kiện điển hình cho các `resist` `DNQ` vạch `g` hoặc vạch `i` dương. Các `resist` `DUV` nói chung sử dụng một `process flow` tương tự với một số thay đổi trong các chi tiết quy trình.

Bước đầu tiên trong quá trình quang khắc là bảo đảm rằng `resist` sẽ bám dính tốt vào wafer. Tùy thuộc vào giai đoạn trong `process flow`, điều này có thể liên quan đến một hay nhiều thao tác. Thông thường, wafer đã sạch ngay trước khi phủ `resist` vì `resist` thường được lắng đọng lên wafer ngay sau khi lắng đọng màng mỏng hoặc ngay sau một bước quy trình nhiệt độ cao nào đó. Nếu không phải vậy, wafer có thể cần được làm sạch hóa học, sử dụng các quy trình mô tả trong Chương `4`. Cũng có thể cần thiết phải nung wafer đến vài trăm `°C` để đuổi hơi nước trên bề mặt. Các bước này được biểu diễn bằng ô đầu tiên trong **Hình 5.31**.

---

**Hình 5.31:** `Process flow` photoresist điển hình cho các `resist` dương `DNQ` vạch `g` và vạch `i`.

---

> **[Process flow]**

| Bước | Mô tả |
|---|---|
| Làm sạch bề mặt và/hoặc nung khử hydrat hóa | Chuẩn bị bề mặt cho việc phủ `photoresist` |
| Phủ `HMDS` | Chất xúc tiến bám dính, thường được phủ quay lên wafer |
| Phủ `resist` | `Resist` được phủ quay lên wafer, thường `3000 - 6000 rpm`, tạo thành lớp `resist` `≈ 0,5 µm` |
| `Prebake resist` | Thường `10 - 30 phút` @ `90 - 100°C` |
| Căn chỉnh wafer, phơi `resist` | Thường được căn chỉnh tại mỗi vị trí phơi, phơi tại `150 mJ cm⁻²` |
| Nung sau phơi (`Post exposure bake`) | Đôi khi được dùng để giảm thiểu sóng dừng trong `resist`; thường `10 phút` @ `100°C` |
| Hiện hình `resist` | Thường `30 - 60 giây` ở nhiệt độ phòng bằng cách phun hoặc nhúng |
| `Postbake resist` | Thường `10 - 30 phút` @ `100 - 140°C` |

---

Ngay cả với bề mặt sạch, khô, sự bám dính của `resist` vào các `IC` silicon có thể không tốt như mong muốn, và do đó việc sử dụng chất xúc tiến bám dính là thực tiễn phổ biến. `Hexamethyldisilane` (`HMDS`) là chất thường dùng nhất cho mục đích này. `HMDS` có thể được phủ lên wafer ở dạng lỏng ở nhiệt độ phòng bằng cách phủ quay trong các điều kiện tương tự như phủ `resist` (`3000 - 6000 rpm` trong `≈ 30 giây`). Tuy nhiên, trong hầu hết các trường hợp, nó được phủ ở dạng hơi với `HMDS` được đưa vào dưới dạng hơi vào một buồng chứa các wafer, vì cách này dễ dàng hơn để tạo ra đơn lớp (`monolayer`) mong muốn trên các wafer. Trong cả hai trường hợp, một đầu của phân tử `HMDS` liên kết dễ dàng với các bề mặt `SiO₂` và đầu kia liên kết với `resist`. Do đó `HMDS` đóng vai trò chất xúc tiến bám dính. Đối với các bề mặt khác với `SiO₂`, các xử lý bám dính khác có thể được sử dụng thêm vào hoặc thay thế cho `HMDS` (Chương `6` của `[5.4]`).

Bước tiếp theo là phủ quay bản thân `resist` lên wafer, và điều này thông thường phải được thực hiện ngay sau khi phủ `HMDS`. `Resist` được phân phối lên wafer và sau đó wafer được quay (`3000 - 6000 rpm` trong `≈ 30 giây`) để tạo ra một lớp mỏng (`≈ 0,6 - 1 µm`) đồng đều. Nếu `resist` sẽ được dùng để che chắn cho một lần cấy ion, nó có thể dày hơn các giá trị này. Mặc dù quy trình nghe có vẻ đơn giản, có một số điểm tinh tế gắn với nó. Việc phân phối `resist` có thể được thực hiện khi wafer đứng yên hoặc khi nó đang quay ở tốc độ chậm để tạo ra một lớp chất lỏng đồng đều trên wafer. Gia tốc của wafer đến tốc độ quay cuối cùng cũng quan trọng và thường được thực hiện nhanh chóng (trong một phần nhỏ của giây). Dung môi trong `resist` bắt đầu bay hơi nhanh sau khi `resist` được phân phối và trong khi nó đang được gia tốc. Nói chung, các màng đồng đều hơn được thu được nếu gia tốc nhanh nhất có thể. Trong vài giây đầu wafer ở tốc độ quay cao, màng san phẳng đến một chiều dày đồng đều. Trong phần còn lại của `≈ 30 giây` quay, dung môi tiếp tục bay hơi để tạo ra chiều dày `resist` cuối cùng. Cơ học lưu chất của quá trình phủ quay đã được nghiên cứu chi tiết `[5.4]`, nhưng quy trình chính xác cho một `resist` cụ thể thường được xác định thực nghiệm. Độ nhớt của `resist` ở trạng thái lỏng (hàm lượng dung môi) và tốc độ quay là các yếu tố chính ảnh hưởng đến chiều dày `resist` cuối cùng. Quá trình quay tạo ra một "gờ cạnh" (`edge bead`), tức là lớp `resist` dày hơn ở ngay rìa wafer, thường cần phải được loại bỏ trước khi tiến hành các bước tiếp theo.

Bước tiếp theo trong quá trình quang khắc là `prebake`. Điều này thường được thực hiện trên một bếp gia nhiệt (`hot plate`) ở `90 - 100°C`. Gia nhiệt bằng tia hồng ngoại hoặc vi sóng cũng có thể được sử dụng, đây là các quy trình nhanh hơn. Bước `prebake` thực hiện được một số điều. Thứ nhất, dung môi còn lại trong `resist` phần lớn bị bay hơi, giảm từ `≈ 25%` xuống còn `≈ 5%` hàm lượng `resist`. Thứ hai, sự bám dính của `resist` được cải thiện vì gia nhiệt tăng cường các liên kết giữa `resist` và `HMDS` cùng đế. Cuối cùng, các ứng suất hiện diện trong `resist` do kết quả của quá trình quay được giải phóng thông qua giãn nở nhiệt. Các biến đổi hóa học có diễn ra trong `resist` trong quá trình nung nhiệt độ cao này với kết quả là thời gian phơi cần thiết tăng lên khi nhiệt độ nung tăng. Cơ chế chịu trách nhiệm cho điều này được cho là sự phân hủy của `PAC` ở nhiệt độ cao với kết quả là độ nhạy của `resist` bị suy giảm. Chúng ta sẽ thảo luận các hiệu ứng này định lượng hơn trong Mục `5.5`.

Quá trình phơi tạo ra một `latent image` trong `resist` có thể được hiện hình về sau. Hầu hết các `resist` thể hiện tính đối ứng (`reciprocity`), có nghĩa là cường độ ánh sáng và thời gian phơi có thể được đổi trực tiếp cho nhau. Do đó, sự tăng cường độ `aerial image` của hệ thống phơi chiếu trực tiếp làm giảm thời gian phơi. Thời gian phơi yêu cầu cũng bị ảnh hưởng bởi chu kỳ nhiệt `prebake` như vừa thảo luận và bởi chiều dày của `resist`. Do đó tất cả các tham số này phải được kiểm soát cẩn thận. Các liều phơi thường được thiết kế để cao hơn đáng kể so với `Qf` (**Hình 5.20**), vì điều này tạo ra các `latent image` trong `resist` có các cạnh sắc nét nhất (dĩ nhiên bị giới hạn bởi chất lượng của `aerial image`). Đối với các `resist` `DNQ` điển hình, điều này tương ứng với liều `> 100 mJ cm⁻²`. Đối với các `resist` `DUV`, sử dụng khuếch đại hóa học, liều thường là `20 - 40 mJ cm⁻²`. Các mô hình chi tiết về quá trình phơi đã được phát triển, bao gồm các hiệu ứng của chất lượng `aerial image`, sóng dừng trong `resist`, v.v. Chúng ta sẽ xem xét các điều này trong Mục `5.5`.

Bước tiếp theo được minh họa trong **Hình 5.31** là nung sau phơi (`post exposure bake`, `PEB`). Trong các `resist` vạch `g` và vạch `i`, bước này đôi khi được thực hiện trước khi hiện hình `latent image` của `resist`, nhằm giảm thiểu các hiệu ứng sóng dừng trong `resist`. Cơ chế là đơn giản. Ở nhiệt độ tăng cao, `PAC` trong các `resist` này có thể khuếch tán. Nếu nhiệt độ và thời gian được kiểm soát tốt trong quá trình nung này, các phân tử `PAC` có thể khuếch tán đủ xa để "làm mờ" các hiệu ứng sóng dừng dọc theo cạnh của các đặc trưng `resist`, nhưng không khuếch tán đủ xa để làm méo đáng kể chính các đặc trưng ảnh. Một chu kỳ nung điển hình có thể là `≈ 10 phút` ở `100°C`. Nếu các lớp phủ chống phản xạ được dùng dưới `resist`, nung sau phơi này có thể không cần thiết vì vấn đề sóng dừng kém nghiêm trọng hơn.

Trong các `resist` `DUV`, `PEB` là một bước cần thiết và quan trọng trong quy trình. Đây là bước mà trong đó `PAG` phản ứng với chuỗi polymer để hoàn tất quá trình phơi. Thời gian và đặc biệt là nhiệt độ phải được kiểm soát rất chặt chẽ vì tốc độ phản ứng hóa học và sự khuếch tán thường phụ thuộc theo hàm mũ vào nhiệt độ.

Các `resist` `DNQ` được hiện hình trong các dung dịch kiềm (thường là dung dịch `TMAH — tetramethyl ammonium hydroxide` pha loãng với `H₂O`, nhưng cũng có thể dùng dung dịch `NaOH` hoặc `KOH`). Dung dịch hiện hình có thể được phủ theo nhiều cách. Các wafer có thể được nhúng vào dung dịch hiện hình, dung dịch hiện hình có thể được phun lên một lô wafer hoặc lên một wafer tại một thời điểm, hoặc một vũng dung dịch hiện hình có thể được đặt lên wafer. Trong mỗi trường hợp, rửa wafer bằng `H₂O` dừng quá trình hiện hình. Tốc độ tiến hành hiện hình phụ thuộc rất nhiều vào nhiệt độ, nồng độ dung dịch hiện hình và tất cả các quy trình phơi và nung được thực hiện trước khi hiện hình. Trong các `resist` `DNQ`, hiện hình tiến hành bằng cách hòa tan axit carboxylic thu được từ `PAC` đã phơi trong dung dịch kiềm. Tốc độ hiện hình phụ thuộc vào nồng độ axit carboxylic cục bộ, vốn tỷ lệ thuận với cường độ phơi cục bộ trong `resist`. Trong các `resist` `DUV` hoạt động dương, hiện hình diễn ra theo cách tương tự vì các chuỗi polymer đã được bỏ chặn hòa tan trong dung dịch hiện hình kiềm. Chúng ta sẽ xem xét các mô hình chi tiết trong Mục `5.5`.

Bước cuối cùng trong quá trình quang khắc là `postbake`. Bước này được thực hiện ở nhiệt độ cao hơn so với các lần nung trước đó (thường `10 - 30 phút` ở `100 - 140°C`), và được thiết kế để làm cứng `resist` và cải thiện khả năng chống khắc của nó. Quá trình nung này khiến `resist` chảy nhẹ và do đó cũng có thể thay đổi các biên dạng cạnh. Bất kỳ dung môi còn lại nào trong `resist` đều bị đuổi bỏ bởi lần nung này và sự bám dính của `resist` với đế bên dưới cũng được cải thiện. Trong một số trường hợp khi `resist` phải chịu đựng một quy trình khắc đặc biệt khắc nghiệt hoặc một lần cấy ion dòng cao có thể làm tăng nhiệt độ của nó đáng kể, việc làm cứng thêm và tạo liên kết ngang (`crosslinking`) của `resist` bằng một lần phơi tử ngoại sâu (`DUV`) diện rộng ở nhiệt độ tăng cao có thể cải thiện độ bền của lớp `resist`.

Trong các quy trình quang khắc hiện đại, nhiều bước mà chúng ta đã mô tả ở trên được thực hiện trong một máy tích hợp duy nhất được gọi là hệ thống `wafer track`. Các máy này có giá `> $1M` và thường được tích hợp chặt chẽ với thiết bị phơi chiếu để dễ dàng chuyển wafer giữa hai hệ thống.

---

## 5.4 Các phương pháp đo

Các vấn đề đo lường gắn với quang khắc có thể được chia thành một số lĩnh vực. Lĩnh vực thứ nhất là bản thân `mask`. Ở đây, chúng ta cần biết kích thước của các đặc trưng trên `mask` và xác minh rằng chúng tương ứng với thiết kế dự định. Nói chung cũng quan trọng là bảo đảm rằng không có khuyết tật nào trên `mask` đủ lớn để in lên wafer trong quá trình phơi.

Như chúng ta đã thấy trong thảo luận trước, việc phân tách quá trình phơi thành hệ quang học tạo ra `aerial image` và xử lý `resist` để chuyển `aerial image` thành biên dạng `resist` là thuận tiện. Bản thân `aerial image` thường không thể đo trực tiếp, do đó các vấn đề đo lường gắn với quang khắc thường tập trung vào mẫu `resist` sau khi được hiện hình. Đây là lĩnh vực chính thứ hai nơi cần có các phương pháp đo. Trong nhiều bước quy trình, dĩ nhiên, mẫu `resist` được chuyển vào các màng mỏng bên dưới hoặc vào bản thân đế silicon bằng khắc, và trong các trường hợp này cũng có nhu cầu đo mẫu đã khắc.

Vấn đề cuối cùng gắn với quá trình quang khắc là sự căn chỉnh các mẫu so với các đặc trưng bên dưới trên wafer (các lớp `mask` trước đó). Như chúng ta đã thấy ở phần trước trong chương này, nói chung các lớp phải được căn chỉnh với dung sai vào cỡ `1/5` đến `1/3` kích thước đặc trưng tối thiểu. Chúng ta sẽ thảo luận một số vấn đề này trong phần này. Một tài liệu tham khảo tuyệt vời về nhiều chủ đề này là `[5.15]`.

---

### 5.4.1 Đo lường các đặc trưng và khuyết tật trên mask

Hầu như tất cả các hệ thống phơi chiếu được sử dụng ngày nay trong sản xuất khối lượng lớn đều là các `stepper` thu nhỏ hoặc các hệ thống chiếu ảnh `step and scan` thu nhỏ. Điều này có nghĩa là `mask` chứa các đặc trưng cho chỉ một vài die và mẫu này được phơi nhiều lần trên mỗi wafer. Nếu có một khuyết tật trên `mask` như vậy, nó sẽ ảnh hưởng đến một phần lớn tất cả các chip trên mỗi wafer mà `mask` được dùng để in. Điều này sẽ dẫn đến các tổn thất `yield` không thể chấp nhận được, và do đó điều tuyệt đối quan trọng là `mask` phải "hoàn hảo". Điều này thực sự có nghĩa là không có khuyết tật nào có thể in được trên `mask`. Vì `mask` có kích thước đặc trưng lớn hơn `4X` đến `5X` so với các mẫu trên wafer, các khuyết tật `mask` nhỏ hơn một kích thước tới hạn nào đó sẽ không in lên wafer. Tuy nhiên, hai vấn đề liên quan đến `mask` là như sau: Mẫu `mask` có tương ứng với thiết kế cho mức `mask` đó không? Và có khuyết tật nào đủ lớn để in lên wafer không?

Mặc dù việc kiểm tra `mask` nhiều năm trước được thực hiện đơn giản bằng cách dùng kính hiển vi, cách tiếp cận như vậy ngày nay không khả thi vì độ phức tạp của các chip hiện đại. Kết quả là, các hệ thống được tự động hóa cao đã được phát triển để thực hiện việc kiểm tra này. Nguyên lý hoạt động được minh họa trong **Hình 5.32**. Ánh sáng đi qua `mask` và được thu nhận bởi một hệ thống tạo ảnh. Nói chung, một cảm biến ảnh trạng thái rắn (`solid state image sensor`) được dùng để phát hiện mẫu của ánh sáng truyền qua. Thông tin này có thể được so sánh với cơ sở dữ liệu thiết kế được dùng để tạo ra `mask`, hoặc với một mẫu `mask` giống hệt thứ hai, nếu `mask` chứa các mẫu cho nhiều hơn một chip. Việc quét hệ thống kiểm tra qua `mask` do đó cung cấp thông tin đầy đủ về các khuyết tật do lỗi trong việc truyền dữ liệu từ cơ sở dữ liệu hoặc do các khuyết tật ngẫu nhiên trên `mask`. Nếu `mask` kết hợp hiệu chỉnh lân cận quang học (`OPC`) hoặc các kỹ thuật nâng cao như dịch pha, quá trình kiểm tra thường khó hơn vì các kỹ thuật này đưa vào các cấu trúc trên `mask` có thể nhỏ hơn kích thước đặc trưng tối thiểu và do đó có thể bị hệ thống kiểm tra giải thích là "khuyết tật."

Nếu các khuyết tật được phát hiện bằng cách tiếp cận này, chúng thường có thể được sửa chữa. Các khuyết tật không trong suốt (`opaque defects`), trong đó chrome hiện diện trên `mask` ở các vùng không nên có, có thể được sửa bằng laser hoặc chùm ion được hội tụ vào vùng khuyết tật và bốc bay phần chrome thừa. Các khuyết tật trong suốt (`clear defects`), trong đó chrome không có ở nơi nó phải có, thường khó sửa hơn vì chúng đòi hỏi phải lắng đọng một vật liệu không trong suốt để che vùng trong suốt. Lắng đọng có hỗ trợ laser (`laser assisted deposition`) từ một khí chứa chromium được đưa vào phía trên `mask` có thể được sử dụng, cũng như lắng đọng bằng chùm ion (`ion beam deposition`).

---

**Hình 5.32:** Hệ thống kiểm tra `mask`. Các hệ thống như vậy hoạt động bằng cách so sánh thông tin đặc trưng trên `mask` với cơ sở dữ liệu thiết kế gốc hoặc với một đặc trưng giống hệt trên một die lân cận. Trong ví dụ này, ba die giống hệt nhau được trình bày trên `mask`.

---

Vấn đề quan trọng cuối cùng liên quan đến `mask` là kích thước thực tế của các đặc trưng trên `mask`. Có một số vấn đề gắn với việc chế tạo `mask` bằng `e-beam` có thể dẫn đến sự chênh lệch về kích thước đặc trưng giữa cơ sở dữ liệu thiết kế và `mask`. Kích thước điểm của `e-beam` là hữu hạn (thường `0,125` đến `0,5 µm`) và điều này có thể quan trọng trong việc ghi các đặc trưng rất nhỏ. Ngoài ra, khi các đặc trưng nhỏ đang được ghi, "các hiệu ứng lân cận" (`proximity effects`) có thể là một vấn đề khi các đặc trưng như vậy ở gần nhau. Các hiệu ứng lân cận phát sinh từ sự tán xạ ngược của electron (`electron backscattering`) trong `resist` trên `mask` và có thể dẫn đến méo mẫu.

Nhiều `mask` ngày nay được chế tạo bằng các hệ thống dựa trên laser thay vì các hệ thống `e-beam` vì các hệ thống dựa trên laser rẻ hơn. Tuy nhiên, các hệ thống dựa trên laser có cùng loại giới hạn độ phân giải như các `stepper` được dùng để chiếu các ảnh lên wafer. Do đó, các đặc trưng được in trên bản thân `mask` có thể bị các góc bo tròn và các hiệu ứng nhiễu xạ khác, giống như trường hợp trong các `aerial image` chiếu lên wafer.

Các kích thước đặc trưng trên `mask` có thể được đo bằng một hệ thống rất giống với hệ trình bày trong **Hình 5.32**. Thay thế bằng cách khác, một camera video và kính hiển vi có thể được dùng trên mặt trên của `mask`. Trong cả hai trường hợp, các kỹ thuật phát hiện cạnh (`edge detection`) được sử dụng trên tín hiệu nhận được để xác định kích thước đặc trưng. Đây là một quy trình tương đối đơn giản trên các `mask` vì lớp chrome mỏng trên `mask` cung cấp một ảnh độ tương phản cao với định nghĩa cạnh tốt. Ngoài ra, các chiều rộng vạch lớn hơn `4X` đến `5X` so với kích thước đặc trưng wafer cuối cùng, vì vậy các phương pháp quang học nói chung hoạt động tốt cho các đặc trưng `mask`. Cục Tiêu chuẩn Quốc gia (`National Bureau of Standards`) có sẵn các tiêu chuẩn chiều rộng vạch có thể được dùng làm tài liệu tham chiếu trong việc đo chính xác các kích thước đặc trưng trên `mask`. Đo chiều rộng vạch không đơn giản như vậy khi đặc trưng nằm trên wafer và `resist` hoặc các cấu trúc màng mỏng khác đang được đo, như chúng ta sẽ thấy trong phần tiếp theo.

### 5.4.2 Đo lường các mẫu resist

Một khi `resist` đã phơi được hiện hình, cấu trúc thực sự là ba chiều như đã được minh họa rõ ràng trong **Hình 5.24**. Các cạnh `resist` có thể bị nghiêng và chúng có thể chứa các mẫu sóng dừng. Do đó, việc định nghĩa và đo lường "chiều rộng vạch" trong `resist` không phải là đơn giản. Khi chiều rộng vạch trong các chip lớn hơn khoảng `1 µm`, các phương pháp quang học sử dụng kính hiển vi và phát hiện cạnh thường được dùng để đo kích thước đặc trưng `resist`. Tuy nhiên, các phương pháp này không thể mở rộng cho các đặc trưng nhỏ trên các chip ngày nay, và kết quả là các phép đo `SEM` đã phần lớn thay thế các phương pháp quang học cho các phép đo chiều rộng vạch chính xác.

Chúng ta đã thảo luận về hoạt động cơ bản của kính hiển vi điện tử trong Chương `3` và `4` (Mục `3.4` và `4.4`). Các phương pháp `SEM` có tiềm năng cho độ phân giải rất cao. Bước sóng điện tử `< 1 nm` ở các điện áp gia tốc điển hình, vì vậy các hiệu ứng nhiễu xạ là không đáng kể. Các `SEM` được thiết kế cho các ứng dụng kiểm tra và đo đạc thường phải hoạt động không phá hủy vì các wafer được dùng để kiểm tra là các wafer sản phẩm. Do đó, lý tưởng là `SEM` hoạt động theo kiểu nội tuyến (`in-line`) như một phần của dây chuyền sản xuất. Các thiết bị như vậy hiện nay đã sẵn có rộng rãi. Chúng nói chung hoạt động với kích thước chùm tia nhỏ (`≈ 10 nm`) và ở điện áp khá thấp (vài `keV`) để giảm thiểu hư hỏng cho các cấu trúc wafer, giảm thiểu các vấn đề tích điện và cho phép tạo ảnh bề mặt `resist`. Chúng nói chung được thiết kế để xử lý các wafer `6"` hoặc `8"` đầy đủ. Hoạt động điện áp thấp cũng giảm thiểu độ sâu mà các electron xuyên vào trong `resist` hoặc các màng mỏng khác và do đó giới hạn các tương tác của electron vào vùng gần bề mặt. Điều này cải thiện khả năng của `SEM` trong việc tạo ảnh các đặc trưng và địa hình bề mặt.

**Hình 5.33** trình bày các ví dụ về các ảnh `SEM` của một mẫu `resist` sau khi hiện hình. Khả năng độ phân giải của kỹ thuật là rõ ràng, nhưng các ảnh này và **Hình 5.24** cũng minh họa một số khó khăn trong việc "đo" chiều rộng vạch trong các cấu trúc như vậy. Khả năng các cạnh bị nghiêng, các mẫu sóng dừng và sự biến thiên chiều rộng vạch dọc theo các vạch `photoresist` đều tạo ra khó khăn trong việc định nghĩa chính xác chiều rộng vạch là gì. Nói chung, chiều rộng vạch được định nghĩa là chiều rộng của vật liệu `photoresist` tại một độ cao cụ thể so với mặt tiếp xúc `resist`-đế. Thường các thuật toán tinh vi được sử dụng để chuyển một đường quét `SEM` thành một "con số" đại diện cho chiều rộng vạch.

---

**Hình 5.33:** Ảnh `SEM` mặt cắt ngang (trái) và nhìn từ trên xuống (phải) của các đặc trưng `photoresist` đã hiện hình, cho thấy các vạch phát triển tốt với các vạch và khe dưới `0,25 µm`. Do A. Vladar và P. Rissman, Hewlett Packard cung cấp.

---

### 5.4.3 Đo lường các đặc trưng đã khắc

Các mẫu `photoresist` thường được chuyển vào các màng mỏng bên dưới bằng khắc, một quá trình được mô tả chi tiết trong Chương `10`. Chất lượng của quá trình chuyển mẫu này rõ ràng cũng quan trọng không kém chất lượng của bản thân mẫu `photoresist`. Các phương pháp đo chiều rộng vạch tương tự, chủ yếu dựa trên `SEM`, được dùng để đo các mẫu đã khắc trong `oxide`, polysilicon, `Al`, hoặc các vật liệu khác.

Không giống như các mẫu `photoresist`, vốn được loại bỏ khỏi wafer sau khi chúng được sử dụng, các mẫu màng mỏng đã khắc vẫn là một phần của chip cuối cùng. Vì lý do này, trong nhiều trường hợp có thể thực hiện các phép đo trên các lớp màng mỏng này sau khi quá trình xử lý wafer hoàn tất. Ngoài các phương pháp `SEM`, thường tiện lợi hơn khi thực hiện các phép đo như vậy về mặt điện trong quá trình kiểm tra wafer. Một lượng công việc đáng kể đã được thực hiện trong những năm gần đây để phát triển các cấu trúc kiểm tra điện (`electrical test structures`) đo các tham số như chiều rộng vạch và độ chính xác căn chỉnh, ngoài các tham số điện linh kiện thông thường hơn `[5.15 - 5.19]`. Các chip kiểm tra hoàn chỉnh đã được phát triển cung cấp thông tin chi tiết về quy trình. Các chip này rất hữu ích trong các giai đoạn phát triển của các quy trình mới. Các cấu trúc kiểm tra cụ thể đôi khi cũng được tích hợp vào các chip sản phẩm khi một quy trình đang trong sản xuất để cung cấp thông tin liên tục về các dung sai sản xuất. Thường các cấu trúc kiểm tra này được đặt trong các vạch cắt (`scribe lines`) giữa các chip để chúng không tiêu thụ diện tích chip.

**Hình 5.34** minh họa ý tưởng cơ bản đằng sau nhiều cấu trúc kiểm tra này. Cấu trúc tổng thể được giả sử là một vật liệu dẫn điện (polysilicon, silicide, nhôm, v.v.). Phần bên phải của cấu trúc này (các pad `3 - 6`) là một cấu trúc `van der Pauw` được thiết kế để trích xuất điện trở tờ (`sheet resistance`) của vật liệu tạo nên cấu trúc kiểm tra. Hình học được chọn để định nghĩa một ô vuông của vật liệu (ký hiệu bằng ký hiệu `ρS` trong hình). Nếu dòng điện `I₅₋₆` được ép giữa các cực `5` và `6`, và điện áp `V₃₋₄` được đo giữa các cực `3` và `4`, thì điện trở tờ được cho đơn giản bởi (xem Phương trình `3.10` ở Chương `3`).

---

> **[Công thức toán]**
>
> $$
> \rho_S = \frac{\pi}{\ln(2)}\frac{V_{3-4}}{I_{5-6}}
> \tag{5.17}
> $$

---

**Hình 5.34:** Cấu trúc kiểm tra được thiết kế để trích xuất điện trở tờ và chiều rộng vạch `W` về mặt điện.

---

Một khi điện trở tờ được đo, chiều rộng vạch `W` có thể được trích xuất từ phần còn lại của cấu trúc thông qua một phép đo điện bổ sung. Trong trường hợp này, dòng điện `I₁₋₅` được ép giữa các cực `1` và `5`, và điện áp `V₂₋₃` được đo giữa các cực `2` và `3`. Chiều rộng vạch `W` khi đó được cho bởi

---

> **[Công thức toán]**
>
> $$
> W = \rho_S L \frac{I_{1-5}}{V_{2-3}}
> \tag{5.18}
> $$

---

Cần lưu ý rằng chiều rộng vạch được trích xuất từ các cấu trúc kiểm tra như thế này có thể khác với chiều rộng vạch được đo quang học hoặc bằng `SEM`. Điều này là vì chiều rộng vạch điện thực sự đo diện tích mặt cắt ngang hiệu dụng mà qua đó dòng điện chảy trong vật liệu. Nếu các cạnh của vật liệu bị nghiêng, hoặc nếu các bề mặt ảnh hưởng đến độ dẫn điện, chiều rộng điện có thể hơi khác so với chiều rộng vật lý được trích xuất từ ảnh của vạch.

Cuối cùng, các biến thể của cấu trúc kiểm tra cơ bản được trình bày trong **Hình 5.34** có thể cho phép các cấu trúc tương tự trích xuất thông tin về độ căn chỉnh giữa các mức trên một chip. Trong trường hợp này, các phần của cấu trúc được chế tạo ở các mức khác nhau của mạch và các phép đo điện trở trong cấu trúc kiểm tra hoàn chỉnh cung cấp thông tin căn chỉnh `[5.17, 5.18]`.

---

## 5.5 Các mô hình và mô phỏng

Mô phỏng quang khắc dựa trên hai lĩnh vực khoa học chính. Lĩnh vực thứ nhất là quang học, cung cấp một mô tả toán học về ứng xử của ánh sáng trong các hệ thống phơi chiếu được sử dụng trong các thiết bị quang khắc hiện đại. Lĩnh vực thứ hai là hóa học, cung cấp các công cụ để xử lý việc phơi, nung và hiện hình của các `resist` được dùng để chuyển đổi `aerial image` được tạo ra bởi hệ thống phơi chiếu thành một bản sao ba chiều của các mẫu `mask`. Nhiều ý tưởng và mô hình cơ bản mà quang học cung cấp về sự lan truyền ánh sáng và các hiệu ứng nhiễu xạ có nguồn gốc trong công trình được thực hiện hơn `100` năm trước bởi Maxwell, Kirchhoff và những người khác. Và dĩ nhiên các ý tưởng cơ bản từ hóa học liên quan đến tốc độ phản ứng hóa học, chất xúc tác và tương tự, cũng là các ý tưởng cũ như vậy.

Tuy nhiên, việc áp dụng các khái niệm này vào quang khắc là một nỗ lực tương đối gần đây, chỉ dating back khoảng `20` năm về giữa những năm `1970`. Công trình tiên phong trong lĩnh vực này bắt đầu tại `IBM` và dẫn đến một loạt các bài báo được trích dẫn rộng rãi của Dill và các cộng sự `[5.20 - 5.23]`. Sau công trình đó, một số nhóm khác đã bắt đầu nghiên cứu mô phỏng quang khắc `[5.24, 5.25]`. Trong mười năm qua, một số công cụ mô phỏng cho quang khắc quang học đã trở nên có sẵn thương mại. Các ví dụ đại diện bao gồm `PROLITH` (Finle Technologies) `[5.3]`, `DEPICT` (Avant!) `[5.26]` và `ATHENA` (Silvaco) `[5.27]`. Các mô hình cơ bản được sử dụng trong mỗi công cụ mô phỏng này là tương tự nhau. Trong các phần sau, chúng ta sẽ mô tả các mô hình này theo cách tổng quát và trình bày các ví dụ cụ thể về việc sử dụng các bộ mô phỏng này trong quang khắc quang học. Như chúng ta đã làm ở phần trước trong chương này, chúng ta sẽ phân chia thảo luận thành sự hình thành `aerial image` (hệ thống phơi chiếu) và xử lý `resist`.

---

### 5.5.1 Các hệ thống phơi chiếu wafer

Vì các hệ thống phơi chiếu chiếu ảnh chi phối thực tiễn công nghiệp ngày nay, hầu hết các công cụ mô phỏng hiện sẵn có áp dụng cho các loại hệ thống này. Do đó, chúng mô hình hóa nhiễu xạ trường xa hay nhiễu xạ Fraunhofer. Một số bộ mô phỏng có khả năng mô phỏng in tiếp xúc hoặc in tiếp cận (`PROLITH` ví dụ), nhưng vì các hệ thống này không được dùng cho sản xuất `VLSI`, chúng ta sẽ không xem xét các công cụ mô phỏng nhiễu xạ trường gần (Fresnel) trong sách này. Người đọc quan tâm được dẫn đến `[5.25]` cho các vấn đề liên quan đến mô phỏng quang khắc tiếp cận hay tiếp xúc.

Cho mục đích thảo luận này, chúng ta sẽ xem xét một hệ quang khắc chiếu ảnh tổng quát như minh họa trong **Hình 5.35**. Mô hình hóa toán học một hệ thống như vậy đòi hỏi một mô tả toán học về ứng xử của ánh sáng. Chúng ta bắt đầu với một mô tả cơ bản về các sóng ánh sáng và sự lan truyền của chúng.

Ánh sáng truyền dưới dạng sóng điện từ. Các điện trường và từ trường vuông góc với nhau và cả hai đều vuông góc với hướng lan truyền sóng. Tuy nhiên, các vật liệu mà photon tương tác trong quang khắc nói chung là phi từ tính (`nonmagnetic`), vì vậy chúng ta có thể xử lý các sóng ánh sáng trong các hệ thống như vậy đơn giản theo nghĩa của một điện trường truyền `ε`. Do đó, một mô tả tổng quát của một sóng ánh sáng đơn sắc đang lan truyền tại một điểm `P` trong không gian đơn giản là

---

> **[Công thức toán]**
>
> $$
> \varepsilon = C\cos(\omega t + \phi)
> \tag{5.19}
> $$

---

trong đó `C` là biên độ, `ω` là tần số và `ϕ` là pha. Chúng ta cũng có thể viết điều này dưới dạng hàm mũ phức.

---

> **[Công thức toán]**
>
> $$
> \varepsilon = \text{Re}\left[C e^{i(\omega t + \phi)}\right]
> \tag{5.20}
> $$

---

**Hình 5.35:** Hệ quang khắc chiếu ảnh tổng quát. Vùng tô bóng bên phải của `mask` minh họa phần của mẫu nhiễu xạ được thu nhận bởi thấu kính chiếu ảnh và được dùng để hình thành `aerial image` của đặc trưng `mask`.

---

Hệ quang khắc chiếu ảnh tổng quát trong **Hình 5.35** bao gồm một số thành phần, mỗi thành phần đã được chúng ta thảo luận trong các phần trước của chương này. Nguồn sáng và thấu kính tụ tạo thành hệ thống chiếu sáng, cần phải truyền ánh sáng tới `mask` với cường độ, độ đồng đều, đặc trưng phổ và độ kết hợp không gian được chỉ định. Một khi ánh sáng đi qua `mask`, các hiệu ứng nhiễu xạ bắt đầu phát huy tác dụng. Thấu kính vật kính hay thấu kính chiếu ảnh được yêu cầu thu nhận nhiều nhất có thể phần ánh sáng bị nhiễu xạ và hội tụ nó lên lớp `resist` trên wafer. Nói chung, sự thu nhỏ ảnh (`demagnification`) cũng diễn ra qua thấu kính vật kính.

Chúng ta sẽ xem `mask` là trong suốt ở một số vùng và hoàn toàn bất trong suốt ở các vùng khác. Đối với các `mask` chrome thường được sử dụng ngày nay, đây là một xấp xỉ rất tốt vì độ tương phản của `mask` rất cao. Do đó trong mặt phẳng `x₁y₁`, chúng ta có thể biểu diễn sự truyền qua của `mask` bằng một hàm số nhị phân đơn giản.

---

> **[Công thức toán]**
>
> $$
> t(x_1, y_1) =
> \begin{cases}
> 0 & \text{vùng bất trong suốt} \\
> 1 & \text{vùng trong suốt}
> \end{cases}
> \tag{5.21}
> $$

---

trong đó `t(x₁,y₁)` là độ truyền qua của `mask`. Nếu các kỹ thuật `mask` nâng cao hơn như dịch pha được sử dụng, thì `t(x₁,y₁)` sẽ biến thiên cả về biên độ lẫn pha và rõ ràng sẽ phức tạp hơn một hàm số nhị phân đơn giản. Chúng ta sẽ xem xét một ví dụ như vậy sau. Sau khi `mask` nhiễu xạ ánh sáng, nó được mô tả bằng tích phân nhiễu xạ Fraunhofer trong miền trường xa. Do đó, tại lối vào của thấu kính vật kính, mẫu cường độ điện trường của ánh sáng được cho bởi `[5.2, 5.3]`

---

> **[Công thức toán]**
>
> $$
> \varepsilon(x', y') = \int_{-\infty}^{+\infty}\int_{-\infty}^{+\infty} t(x_1, y_1)\, e^{-2\pi j(f_x x + f_y y)}\, dx\, dy
> \tag{5.22}
> $$

---

Trong biểu thức này, các số hạng `fₓ` và `f_y` được gọi là các tần số không gian của mẫu nhiễu xạ và được định nghĩa là

---

> **[Công thức toán]**
>
> $$
> f_x = \frac{x'}{z\lambda} \quad \text{và} \quad f_y = \frac{y'}{z\lambda}
> \tag{5.23}
> $$

---

trong đó `z` là khoảng cách từ `mask` đến thấu kính. Phương trình `5.22` đơn giản là phép biến đổi Fourier của mẫu `mask`. Mẫu cường độ ánh sáng vào thấu kính vật kính do đó có thể được tính toán bằng các phương pháp đã biết từ lĩnh vực quang học Fourier. Theo ký hiệu tắt của phép biến đổi Fourier, chúng ta có thể viết lại Phương trình `5.22` là

---

> **[Công thức toán]**
>
> $$
> \varepsilon(f_x, f_y) = \mathcal{F}\{t(x_1, y_1)\}
> \tag{5.24}
> $$

---

trong đó `F` đại diện cho phép biến đổi Fourier. `fₓ` và `f_y` đơn giản là các tọa độ không gian được co giãn trong mặt phẳng `x', y'`. Phân bố cường độ của ánh sáng là bình phương của biên độ điện trường, sao cho

---

> **[Công thức toán]**
>
> $$
> I(f_x, f_y) = \left|\varepsilon(f_x, f_y)\right|^2 = \left|\mathcal{F}\{t(x_1, y_1)\}\right|^2
> \tag{5.25}
> $$

---

## Ví Dụ:

Xét một mẫu `mask` đơn giản là một khe chữ nhật dài có chiều rộng `w` (**Hình 5.36**). Tìm mẫu cường độ quang học thu được trong miền trường xa (Fraunhofer).

### Lời Giải:

Phép biến đổi Fourier của hàm `t(x)` được tìm thấy trong các sách giáo khoa tiêu chuẩn `[5.2]`

---

> **[Công thức toán]**
>
> $$
> \varepsilon(x') = \mathcal{F}\{t(x)\} = \frac{\sin(\pi w f_x)}{\pi f_x}
> \tag{5.26}
> $$

---

Phân bố cường độ quang học thu được là bình phương của hàm này và cũng được vẽ trong **Hình 5.36**. Điểm không đầu tiên của cường độ xảy ra tại

---

> **[Công thức toán]**
>
> $$
> f_x = \frac{1}{\pi w} \quad \text{hay} \quad x' = \frac{z\lambda}{\pi w}
> \tag{5.27}
> $$

---

Do đó, ảnh của khe trải rộng ra khi chúng ta di chuyển xa hơn khỏi `mask` (`z` tăng). Ảnh cũng trải rộng hơn khi sử dụng bước sóng ánh sáng dài hơn. Cả hai kết quả này đều được kỳ vọng dựa trên thảo luận trước của chúng ta về nhiễu xạ. Có lẽ trái với trực giác, ảnh trải rộng hơn khi khe nhỏ hơn (khi `w` giảm). Điều này đã được thảo luận trong mối liên hệ với **Hình 5.5** trước đó.

---

**Hình 5.36:** Khẩu độ chữ nhật trong một `mask` và mẫu nhiễu xạ Fraunhofer trường xa thu được cùng mẫu cường độ quang học.

---

Bây giờ chúng ta quay lại hệ quang khắc tổng quát trong **Hình 5.35**. Khi ánh sáng bị nhiễu xạ đi qua mặt phẳng `x'y'`, nó đi vào thấu kính vật kính. Lưu ý rằng chỉ một phần của ánh sáng bị nhiễu xạ được thu nhận bởi thấu kính vì kích thước hữu hạn của nó. Chúng ta đã đặc trưng điều này thông qua `NA` trong thảo luận trước. Chức năng của thấu kính vật kính là tái tạo mẫu nhiễu xạ và hội tụ nó lên wafer. Vì mẫu cường độ ánh sáng tại mặt phẳng `x'y'` đơn giản là phép biến đổi Fourier của mẫu `mask`, thấu kính vật kính thực sự cần phải thực hiện phép biến đổi Fourier ngược. Đây thực ra chính xác là điều mà các thấu kính cầu thực hiện. Thấu kính chỉ có thể thực hiện phép tính này trên phần ánh sáng bị nhiễu xạ đi vào thấu kính, và theo nghĩa này chúng ta gọi ảnh mà thấu kính tạo ra là ảnh "bị giới hạn bởi nhiễu xạ" (`diffraction limited`).

Chúng ta có thể đặc trưng phần ánh sáng bị nhiễu xạ mà thấu kính vật kính thu nhận bằng một "hàm đồng tử" (`pupil function`) `P` được định nghĩa là

---

> **[Công thức toán]**
>
> $$
> P(f_x, f_y) =
> \begin{cases}
> 1 & \text{nếu } f_x^2 + f_y^2 < \left(\dfrac{NA}{\lambda}\right)^2 \\[6pt]
> 0 & \text{nếu } f_x^2 + f_y^2 > \left(\dfrac{NA}{\lambda}\right)^2
> \end{cases}
> \tag{5.28}
> $$

---

vì đối với các góc nhỏ, các tần số không gian `fₓ` và `f_y` được cho bởi

---

> **[Công thức toán]**
>
> $$
> f_x = \frac{x'}{z\lambda} \approx \frac{\sin\alpha}{\lambda} = \frac{NA}{\lambda}
> \tag{5.29}
> $$

---

`P` có thể bị giới hạn bởi kích thước vật lý của thấu kính vật kính, hoặc bởi một khẩu độ đặt trước thấu kính. Dù bằng cách nào, thông tin đi qua thấu kính vật kính thực sự được lọc thông thấp (`low pass filtered`) bởi hàm đồng tử `P`. Các tần số không gian cao hơn `NA/λ` đơn giản là không được truyền tới ảnh trên wafer. Sự tương tự trong các mạch điện — một xung sắc nét đi qua một bộ lọc thông thấp sẽ có các cạnh bị bo tròn — có thể giúp giải thích sự suy giảm quang học trong `aerial image` gây ra bởi `P`. Một vật thể được định nghĩa sắc nét trên `mask` được tạo ảnh trên wafer với các cạnh "bị nhòe", và các góc sắc trở nên bị bo tròn.

Thấu kính vật kính bây giờ thực hiện hàm biến đổi Fourier ngược trên phần ánh sáng bị nhiễu xạ mà nó thu nhận. Do đó, tại mặt phẳng ảnh trên wafer (bề mặt `resist`), điện trường gắn với mẫu ánh sáng được cho bởi

---

> **[Công thức toán]**
>
> $$
> \varepsilon(x, y) = \mathcal{F}^{-1}\{\varepsilon(f_x, f_y)\cdot P(f_x, f_y)\}
> = \mathcal{F}^{-1}\{\mathcal{F}\{t(x_1, y_1)\}\cdot P(f_x, f_y)\}
> \tag{5.30}
> $$

---

Cuối cùng, cường độ của phân bố ánh sáng tại bề mặt `resist` `Iᵢ(x,y)` đơn giản được cho bởi

---

> **[Công thức toán]**
>
> $$
> I_i(x, y) = \left|\varepsilon(x, y)\right|^2
> \tag{5.31}
> $$

---

Phương trình `5.31` bây giờ đại diện cho `aerial image` được tạo ra bởi hệ thống phơi chiếu. **Hình 5.37** tóm tắt các mô hình toán học được sử dụng để mô tả hệ thống phơi chiếu.

Trong các hệ quang khắc chiếu ảnh thực, có một số vấn đề bổ sung phải được xem xét trong việc tính toán `aerial image`. Chúng ta đã thảo luận các vấn đề này định tính hơn ở phần trước trong chương này, nhưng bây giờ chúng ta cần định lượng chúng để cho phép mô phỏng trong các hệ thống thực. Các vấn đề thường quan trọng trong các hệ tạo ảnh thực bao gồm chiếu sáng lệch trục, việc sử dụng nguồn sáng kết hợp một phần, các sai lệch trong hệ thấu kính, các vấn đề độ sâu tiêu cự và chiều dày hữu hạn của `photoresist`, có nghĩa là `aerial image` phải được xác định trên một thể tích nào đó, không chỉ tại bề mặt `resist`. Chúng ta sẽ mô tả trong các đoạn sau các sửa đổi mà chúng ta cần thực hiện đối với Phương trình `5.31` để xử lý các vấn đề này.

Các vấn đề đầu tiên là chiếu sáng lệch trục và các nguồn sáng kết hợp một phần. Trong cả hai trường hợp, ánh sáng vào `mask` không có hướng vuông góc với `mask`. Kết quả của điều này (**Hình 5.30**) là vị trí của mẫu nhiễu xạ bị dịch chuyển trong mặt phẳng `x'y'` tại lối vào của thấu kính vật kính. Nếu ánh sáng vào `mask` ở một góc `θ`, thì theo các tần số không gian `fₓ` và `f_y`, mẫu nhiễu xạ bị dịch chuyển một lượng `sinθ/λ`. Kết quả khi đó là điện trường gắn với mẫu ánh sáng trong mặt phẳng ảnh được biểu diễn là `[5.3]`

---

> **[Công thức toán]**
>
> $$
> \varepsilon(x, y, f'_x, f'_y)
> = \mathcal{F}^{-1}\{\varepsilon(f_x - f'_x,\; f_y - f'_y)\cdot P(f_x, f_y)\}
> \tag{5.32}
> $$
>
> $$
> I_i(x, y, f'_x, f'_y)
> = \left|\varepsilon(x, y, f'_x, f'_y)\right|^2
> \tag{5.33}
> $$

---

**Hình 5.37:** Các mô hình toán học được sử dụng để mô tả hệ thống phơi chiếu chiếu ảnh tại mỗi điểm trong không gian.

---

Trong trường hợp nguồn kết hợp một phần, ánh sáng vào `mask` từ nhiều góc độ khác nhau. Điều này thường được xử lý bằng nguyên lý chồng chập `[5.27]`. Nguồn được chia thành các nguồn điểm riêng lẻ và các cường độ của ánh sáng tại mặt phẳng ảnh do mỗi nguồn điểm được cộng lại. Được biểu diễn theo toán học, nếu `S(f'ₓ, f'_y)` là hàm mô tả cường độ nguồn theo vị trí hay góc, thì `[5.3]`

---

> **[Công thức toán]**
>
> $$
> I_{total}(x, y)
> =
> \frac{
> \displaystyle\iint_{\text{source}} I(x, y, f'_x, f'_y)\, S(f'_x, f'_y)\, df'_x\, df'_y
> }{
> \displaystyle\iint_{\text{source}} S(f'_x, f'_y)\, df'_x\, df'_y
> }
> \tag{5.34}
> $$

---

trong đó `Itotal` là tổng thông lượng ánh sáng tác động lên bề mặt `resist`. Phương trình `5.34` do đó cho phép tính toán `aerial image` đối với một chiếu sáng nguồn tùy ý.

Các sai lệch hay khuyết tật (`aberrations`) luôn hiện diện trong các hệ thấu kính thực. Chúng phát sinh từ các dung sai chế tạo, các thay đổi cơ học trong một hệ thống trong quá trình sử dụng (các thấu kính lệch trục với nhau), và từ thực tế là không thể thiết kế một thấu kính hoàn hảo hoàn toàn không có sai lệch. Mặc dù các vấn đề như vậy có thể được mô hình hóa theo nhiều cách, phương pháp phổ biến nhất là xem mặt sóng ra khỏi thấu kính như có một sai số về pha hay độ lệch đường đi, so với một thấu kính lý tưởng không sai lệch. Sai số trong một thấu kính thực tế sẽ là hàm số của vị trí dọc theo mặt sóng và thường được biểu diễn bằng tọa độ cực vì các thấu kính nói chung là tròn. Sai số pha thường được biểu diễn như một đa thức Zernike `W(R,θ)`, có thể có nhiều số hạng `[5.3]`. `W(R,θ)` là độ lệch chiều dài đường đi giữa một thấu kính lý tưởng và một thấu kính có sai lệch. Ảnh hưởng của các sai lệch này lên `aerial image` được đưa vào bằng cách hiệu chỉnh hàm đồng tử

---

> **[Công thức toán]**
>
> $$
> P(f_x, f_y) = P_{ideal}(f_x, f_y)\cdot e^{2\pi j W(R,\theta)}
> \tag{5.35}
> $$

---

Do đó nếu `W(R,θ)` đã biết, `aerial image` có thể được tính toán bao gồm các hiệu ứng của sai lệch thấu kính.

Nếu `resist` không nằm vật lý trong mặt phẳng tiêu cự của thấu kính vật kính, sẽ xảy ra thêm sự suy giảm ảnh. Các hiệu ứng này cũng có thể được xử lý như một sai số pha trong mặt sóng ra khỏi thấu kính vật kính `[5.2, 5.26]`. Do đó, chúng có thể được xử lý toán học theo cùng cách như các sai lệch thấu kính (Phương trình `5.35`). Trong trường hợp mất tiêu cự (`defocus`), sai số chiều dài đường đi có thể được tính toán như minh họa trong **Hình 5.38**.

---

**Hình 5.38:** Biểu diễn mất tiêu cự `δ` như một sai số trong chiều dài đường đi quang học (`OPD — optical path difference`).

---

Ở đây, chúng ta tưởng tượng rằng nếu ảnh được hội tụ đúng tại bề mặt `resist`, ánh sáng sẽ đã xuất phát từ một thấu kính vật kính có bán kính cong lớn hơn (các đường nét đứt) thay vì từ thấu kính thực. Độ lệch đường đi quang học (`OPD`) bằng không tại tâm thấu kính và cực đại tại bán kính ngoài của thấu kính. Nếu `R >> δ`, thì

---

> **[Công thức toán]**
>
> $$
> OPD \approx \delta(1 - \cos\theta)
> \tag{5.36}
> $$

---

Biểu thức này sau đó có thể được sử dụng trong Phương trình `5.35` để tính toán ảnh hưởng lên `aerial image` do mất tiêu cự. Lưu ý rằng `OPD` là lớn nhất ở các cạnh của thấu kính, nơi phần ánh sáng bị nhiễu xạ bậc cao hơn đi qua. Đây là ánh sáng chứa thông tin chi tiết về hình dạng `mask`, vì vậy mất tiêu cự rõ ràng sẽ làm suy giảm chất lượng của `aerial image`.

Có một số công cụ mô phỏng thương mại sẵn có triển khai các mô hình mà chúng ta vừa mô tả. Nói chung, `mask` được mô tả hoặc như một tổ hợp các hình chữ nhật hoặc như một cấu trúc hình học tùy ý. Trong một số trường hợp, thông tin `mask` trực tiếp từ cơ sở dữ liệu thiết kế có thể được tải xuống vào công cụ mô phỏng quang khắc. Dù được thực hiện bằng cách nào, hàm truyền qua `t(x₁, y₁)` phải được người dùng chỉ định. Thiết bị phơi chiếu được mô tả theo `NA`, bước sóng chiếu sáng `λ`, mức độ kết hợp của nguồn, bất kỳ sự mất tiêu cự nào hiện diện, và bất kỳ sai lệch nào trong thấu kính. Các công cụ mô phỏng sau đó tính toán `aerial image` bằng cách sử dụng các phương trình từ quang học Fourier mà chúng ta đã mô tả. Các **Hình 5.39 - 5.41** trình bày các ví dụ về các loại mô phỏng có thể được thực hiện với các công cụ này. Đặc biệt khi chiều rộng vạch thu nhỏ và các thiết bị quang khắc hoạt động gần hơn với các giới hạn vật lý của chúng, các bộ mô phỏng trở nên thiết yếu để hiểu và dự đoán các chi tiết của `aerial image` được tạo ra trong quá trình phơi.

**Hình 5.39:** Ví dụ tính toán `aerial image` sử dụng bộ mô phỏng `ATHENA` của Silvaco. Màu sắc tô bóng tương ứng với cường độ quang học trong `aerial image`. Các đường viền đen tương ứng với ảnh `mask` đang được in. Hệ thống phơi chiếu được mô phỏng có `NA = 0,43`, chiếu sáng vạch `g` kết hợp một phần (`λ = 436 nm`) và không có sai lệch hay mất tiêu cự nào khác. Kích thước đặc trưng tối thiểu là `1 µm`.

---

**Hình 5.40:** Ví dụ giống như trong **Hình 5.39** ngoại trừ kích thước đặc trưng đã được giảm xuống `0,5 µm`. Lưu ý chất lượng ảnh kém hơn nhiều.

---

**Hình 5.41:** Ví dụ giống như trong **Hình 5.40** ngoại trừ bước sóng chiếu sáng bây giờ đã được thay đổi thành chiếu sáng vạch `i` (`λ = 365 nm`) và `NA` đã được tăng lên `0,5`. Lưu ý sự cải thiện về chất lượng ảnh thu được từ bước sóng phơi ngắn hơn và hệ thống `NA` cao hơn.

---

### 5.5.2 Mẫu cường độ quang học trong photoresist

`Aerial image` được tính toán ở trên là cường độ quang học trong không khí ngay phía trên bề mặt của `photoresist`. Bước thứ hai trong việc mô phỏng hiệu năng của các thiết bị quang khắc là tính toán mẫu cường độ quang học xuyên qua lớp `photoresist` như minh họa trong **Hình 5.42**. Một khi điều này được thực hiện, chúng ta sau đó có thể tính toán phản ứng hóa học của `resist` và do đó cấu trúc ba chiều của `resist` sau khi mẫu của nó được hiện hình.

Mẫu cường độ quang học xuyên qua lớp `resist` sẽ khác với `aerial image` vì một số lý do. Thứ nhất, `resist` có chiều dày hữu hạn và do đó ảnh được tạo bởi hệ quang học không thể hội tụ hoàn hảo ở mọi nơi trong `resist`. Một vấn đề tiềm ẩn khác là sự hiện diện của các sóng dừng trong `resist`, gây ra bởi sự phản xạ ánh sáng từ các cấu trúc bên dưới. Chúng ta đã minh họa vấn đề này trong các **Hình 5.23** và **5.24**. Ngoài ra, như chúng ta cũng đã thảo luận trong mối liên hệ với **Hình 5.22**, sự hấp thụ ánh sáng trong các `resist` `DNQ` điển hình thay đổi như thế nào theo thời gian phơi do tẩy trắng. Điều này dẫn đến một cường độ ánh sáng biến thiên theo độ sâu và theo thời gian trong `resist`. Cuối cùng, trong các hệ thống phơi chiếu `NA` cao, không phải tất cả ánh sáng tác động lên `resist` đều chiếu thẳng đứng. Điều này làm phức tạp việc tính toán bất kỳ mẫu sóng dừng nào có thể hiện diện trong `resist` và nói chung đòi hỏi phải thực hiện tích phân trên tổng góc của ánh sáng tới. Quy trình này cũng có thể bao gồm các hiệu ứng của độ kết hợp một phần trong nguồn sáng vì điều này cũng dẫn đến ánh sáng tác động lên `resist` ở các góc không vuông góc.

Cách đơn giản nhất để giải quyết nhiều vấn đề này là sửa đổi Phương trình `5.31` như sau:

---

> **[Công thức toán]**
>
> $$
> I(x, y, z) = I_i(x, y)\cdot I_r(x, y, z)
> \tag{5.37}
> $$

---

`Iᵢ(x,y)` lại là mẫu cường độ ánh sáng chiếu lên bề mặt trên của `resist` (`aerial image` được cho bởi Phương trình `5.31`) và `Iᵣ(x,y,z)` là một hệ số hiệu chỉnh bao gồm các hiệu ứng của mất tiêu cự, sóng dừng và tẩy trắng `resist`.

---

**Hình 5.42:** Chuyển đổi `aerial image` thành phân bố cường độ ánh sáng xuyên qua lớp `resist`. Đây là `latent image` được tạo ra trong `photoresist` bởi các photon phơi. Các hiệu ứng sóng dừng, mất tiêu cự và tẩy trắng đều góp phần làm cho `I(x,y,z)` khác với `Iᵢ(x,y)`.

---

Sự mất tiêu cự của ảnh xuyên qua lớp `resist` có thể được giải quyết thông qua các Phương trình `5.35` và `5.36`. Nếu `aerial image` được hội tụ tại bề mặt trên của `resist`, thì sự mất tiêu cự xảy ra xuyên qua chiều dày `resist` được cho bởi

---

> **[Công thức toán]**
>
> $$
> \delta(z) = \frac{z}{n}
> \tag{5.38}
> $$

---

trong đó `z` là độ sâu vào trong `resist` và `n` là chiết suất của vật liệu `resist`. Hệ số này sau đó có thể được đưa vào Phương trình `5.37` thông qua việc sử dụng hàm đồng tử (Phương trình `5.35`). Phương trình `5.38` giả sử ánh sáng chiếu thẳng góc. Tuy nhiên, một cách tiếp cận tương tự có thể được dùng để tính đến ánh sáng không chiếu thẳng góc.

Các sóng dừng trong `resist` cũng có thể được giải quyết theo một cách khái niệm đơn giản. Hãy xét **Hình 5.43**, trong đó `nⱼ` là chiết suất của mỗi lớp, và `ε` là điện trường trong mỗi lớp do một sóng phẳng điện từ đơn sắc chiếu thẳng góc. Sự phản xạ từ mặt tiếp xúc `resist`-đế dẫn đến một sóng phản xạ, và tổng điện trường trong `resist` là tổng của hai sóng phẳng truyền ngược chiều nhau. Nếu không có sự suy giảm biên độ sóng khi nó đi qua lớp `2` (`resist`) theo cả hai hướng, thì mẫu sóng dừng thu được sẽ có các nút (`nodes`) nơi biên độ tổng bằng không và các bụng (`antinodes`) nơi biên độ tổng bằng hai lần biên độ sóng tới. Tổng quát hơn, có tính đến sự suy giảm trong lớp `resist`, sóng dừng thu được được mô tả bởi một nghiệm của các phương trình Maxwell với các điều kiện biên thích hợp tại mỗi mặt tiếp xúc. Mack đã chỉ ra rằng trong hệ thống này, sóng dừng có thể được mô tả bởi `[5.25]`

---

> **[Công thức toán]**
>
> $$
> \varepsilon_2(x,y,z)
> = \varepsilon_1(x,y)\cdot
> \frac{\tau_{12}\!\left(e^{-2\pi j n_2 z/\lambda} + \rho_{23}\,\tau_D^2\, e^{+2\pi j n_2 z/\lambda}\right)}
> {1 + \rho_{12}\,\rho_{23}\,\tau_D^2}
> \tag{5.39}
> $$
>
> trong đó:
>
> $$
> \rho_{ij} = \frac{n_i - n_j}{n_i + n_j}, \quad \text{hệ số phản xạ tại mặt tiếp xúc } i
> $$
>
> $$
> \tau_{ij} = \frac{2n_i}{n_i + n_j}, \quad \text{hệ số truyền qua tại mặt tiếp xúc}
> $$
>
> $$
> \tau_D = \exp(-jk_2 D), \quad \text{độ truyền qua của màng } \text{resist}
> $$
>
> $$
> k_j = \frac{2\pi n_j}{\lambda}, \quad \text{hằng số lan truyền của lớp } j
> $$

---

trong đó `ε₁(x,y)` là sóng phẳng điện từ tới, `ε₂(x,y,z)` là sóng phẳng trong `resist`, `nⱼ` là chiết suất phức của lớp `j`, `λ` là bước sóng của ánh sáng tới. Cường độ ánh sáng trong `resist` đơn giản là bình phương của biên độ của `ε₂(x,y,z)`.

---

**Hình 5.43:** Ví dụ đơn giản về sự hình thành sóng dừng trong một lớp `resist`.

---

Việc tính toán thực tế mẫu sóng dừng trong một cấu trúc `IC` thực phức tạp hơn đáng kể so với những gì Phương trình `5.39` có thể gợi ý. Nói chung, sẽ có nhiều lớp (một số trong suốt quang học như `SiO₂` và một số bất trong suốt như `Al`) bên dưới `resist`, và bản thân chiều dày `resist` thường biến thiên theo vị trí. Hơn nữa, ánh sáng tới thường không chiếu thẳng góc và trong một số hệ thống phơi chiếu nó thậm chí có thể không đơn sắc. Tuy nhiên, lý thuyết quang học cơ bản có thể được dùng để tính toán `ε₂(x,y,z)` tại mỗi điểm trong `resist` ngay cả với tất cả các phức tạp bổ sung này `[5.3, 5.26, 5.27]`.

Một ví dụ về mô phỏng như vậy được trình bày trong **Hình 5.44**. Một cấu trúc tương đối đơn giản được định nghĩa với một đế silicon được khắc để tạo thành một bậc có mặt nghiêng. Lớp `photoresist` được lắng đọng sao cho nó có bề mặt trên phẳng và do đó chiều dày của nó biến thiên theo cấu trúc. Một `mask` được định nghĩa cho phép ánh sáng vào ở phần trung tâm của cấu trúc (`x = 1` đến `x = 2 µm`). Phần dưới của **Hình 5.44** minh họa nồng độ `PAC` của `resist` `DNQ` được tính toán sau khi phơi. Như chúng ta sẽ thấy trong phần tiếp theo về động học phơi `resist`, biên dạng nồng độ `2D` này tương ứng với biên dạng cường độ ánh sáng tích phân xuyên qua quá trình phơi. Có một số đặc điểm thú vị có thể quan sát được từ mô phỏng này.

---

**Hình 5.44:** Ví dụ tính toán phân bố cường độ ánh sáng trong một lớp `photoresist` trong quá trình phơi sử dụng bộ mô phỏng `ATHENA` của Silvaco. Một cấu trúc đơn giản được định nghĩa ở trên với một lớp `photoresist` phủ lên một đế silicon có hai vùng phẳng và một vách nghiêng. Việc phơi diễn ra giữa `x = 1` và `x = 2 µm`. Mô phỏng ở dưới cho thấy nồng độ `PAC` của `resist` `DNQ` được tính toán sau một lần phơi `200 mJ cm⁻²`. Giá trị `PAC` thấp hơn tương ứng với sự phơi nhiều hơn. Do đó, các đường đồng mức thang xám tương ứng với cường độ ánh sáng tích phân từ quá trình phơi.

---

Thứ nhất, lưu ý ở phía bên trái của vùng đã phơi các hiệu ứng của sóng dừng trong cường độ ánh sáng. Đế silicon trong ví dụ này là một đế phản xạ và do đó các sóng dừng sẽ được thiết lập. Các nút cường độ ánh sáng cực đại tương ứng với các cực tiểu trong `PAC` (phơi cực đại). Đây là các dải tối ở bên trái. Chúng xuất hiện tại các khoảng cách `λ/2n`. Các nút cường độ ánh sáng cực tiểu (nồng độ `PAC` cực đại) cũng xuất hiện với chu kỳ `λ/2n` và là các dải xám nhạt. Cũng lưu ý hiệu ứng của vách nghiêng ở phần trung tâm của cấu trúc. Ở đây, các sóng ánh sáng tới bị phản xạ về phía phải, thiết lập một mẫu sóng dừng song song với vách nghiêng. Ngoài mẫu sóng dừng này, các sóng ánh sáng phản xạ sẽ làm cho vùng đã phơi mở rộng vào vùng che bên phải. Điều này sẽ dẫn đến suy giảm ảnh. Chúng ta sẽ quay lại ví dụ này sau để xem các hiệu ứng của nung sau phơi và hiện hình `resist` lên cấu trúc `resist` cuối cùng. Hiện tại, cần rõ ràng rằng các công cụ mô phỏng số là cần thiết để giải quyết độ phức tạp của các cấu trúc gặp phải trong các `IC` hiện đại.

Vấn đề cuối cùng liên quan đến phân bố cường độ ánh sáng xuyên qua `photoresist` là tẩy trắng `resist`. Như chúng ta đã thấy trước đó, điều này xảy ra trong các `resist` `DNQ` vì `PAC` trong các `resist` này ban đầu hấp thụ các photon khi đang bị phơi, và sau đó trở nên truyền qua nhiều hơn khi thành phần `PAC` được chuyển đổi thành axit carboxylic. Do đó, các lớp trên cùng của `resist` ban đầu hấp thụ các photon tới và sau đó trong quá trình phơi cho phép nhiều ánh sáng hơn thâm nhập tới các lớp sâu hơn của `resist`. Điều này dẫn đến một cường độ ánh sáng phụ thuộc thời gian xuyên suốt `resist`. Vì vấn đề này liên quan trực tiếp đến hóa học phơi `resist`, chúng ta sẽ thảo luận các mô hình cho nó trong phần tiếp theo về phơi `resist`. Về mặt định tính, các hiệu ứng của quá trình tẩy trắng này có thể quan sát được ở phần dưới của **Hình 5.44**, nơi trung bình cho thấy sự tăng dần nồng độ `PAC` theo độ sâu vào trong `resist`.

---

### 5.5.3 Phơi photoresist

Trong phần này cho đến cuối của nó, chúng ta sẽ bỏ qua bất kỳ sóng dừng nào có thể hiện diện trong `resist`. Các hiệu ứng này có thể dễ dàng được đưa vào mô hình phơi sử dụng Phương trình `5.39` và chúng ta sẽ bao gồm các hiệu ứng như vậy trong các ví dụ mô phỏng ở cuối phần. Tuy nhiên, các ý tưởng nguyên lý của phơi `photoresist` có thể được hiểu mà không cần sự phức tạp của sóng dừng, và đó là cách tiếp cận mà chúng ta sẽ ban đầu thực hiện ở đây. Chúng ta cũng sẽ, vào lúc này, chỉ đơn giản xem xét một cấu trúc một chiều với một lớp `resist` đồng đều đang được phơi.

#### 5.5.3.1 Resist DNQ vạch g và vạch i

Ánh sáng chiếu lên `photoresist` chủ yếu được hấp thụ bởi thành phần `PAC` của `resist`. `PAC` được giả sử phân bố đồng đều xuyên suốt `resist`. Như chúng ta đã thấy, sự tẩy trắng xảy ra từ các lớp trên cùng của `resist` xuống dưới khi `PAC` được phơi. Phương trình cơ bản mô tả sự hấp thụ ánh sáng được cho bởi

---

> **[Công thức toán]**
>
> $$
> \frac{dI}{dz} = -\alpha I
> \tag{5.40}
> $$

---

trong đó `z` là hướng vào trong `resist`. Phương trình này về cơ bản phát biểu rằng xác suất một photon bị hấp thụ tỷ lệ thuận với cường độ ánh sáng, với `α` là hệ số hấp thụ, là hằng số tỷ lệ. Nếu `α` là hằng số, tích phân của phương trình này cho kết quả là Phương trình `5.15`, mà chúng ta đã trình bày trước đó như một mô tả đơn giản về cách cường độ ánh sáng giảm dần trong `photoresist` theo độ sâu.

`α` sẽ hóa ra liên quan đến nồng độ của `PAC`, vốn chưa được phơi trong `resist` tại một thời điểm và vị trí cụ thể. Do đó `α` không phải là hằng số, mà là một hàm số của vị trí và thời gian. Tại bất kỳ thời điểm nào trong quá trình phơi, biên dạng cường độ ánh sáng trong `resist` sẽ được cho bởi

---

> **[Công thức toán]**
>
> $$
> I(z) = I_0 \exp\!\left(-\int_0^z \alpha(z')\, dz'\right)
> \tag{5.41}
> $$

---

trong đó tích phân trong số mũ là độ hấp thụ của `resist` xuống tới độ sâu `z`.

Bây giờ chúng ta cần liên hệ `α` với các tính chất vật liệu của `resist`. Nếu thành phần `PAC` của `resist` là loãng, thì hệ số hấp thụ của `resist` đơn giản là

---

> **[Công thức toán]**
>
> $$
> \alpha_{resist} = \alpha_{PAC}[\text{PAC}]
> \tag{5.42}
> $$

---

trong đó `[PAC]` là nồng độ của thành phần `PAC` trong `resist` và `α_PAC` là hệ số hấp thụ của vật liệu `PAC`. Phương trình `5.42` đơn giản phát biểu rằng sự hấp thụ của `resist` được xác định bởi lượng `PAC` trong `resist`. Xấp xỉ loãng cần thiết cho Phương trình `5.42` đã được chứng minh là đúng đối với các thành phần `resist` thực tế `[5.29]`.

Các `resist` `DNQ` bao gồm một số thành phần như chúng ta đã thấy trước đó trong chương này. Nói chung, các `resist` như vậy sẽ có một nhựa `R` (thường là `novolac`), một thành phần quang hoạt `PAC`, một dung môi `S`, và khi quá trình phơi tiến hành, các sản phẩm phơi `P` (chủ yếu là axit carboxylic được tạo ra từ `PAC`). Tổng quát hơn, Phương trình `5.42` có thể được viết là

---

> **[Công thức toán]**
>
> $$
> \alpha_{resist} = \alpha_{PAC}[\text{PAC}] + \alpha_R[R] + \alpha_S[S] + \alpha_P[P]
> \tag{5.43}
> $$

---

Vì các sản phẩm phơi thu được từ `PAC`, chúng ta có thể viết rằng

---

> **[Công thức toán]**
>
> $$
> [P] = [\text{PAC}]_0 - [\text{PAC}]
> \tag{5.44}
> $$

---

Theo cách tiếp cận của `[5.21]`, chúng ta viết lại Phương trình `5.43` theo dạng sau

---

> **[Công thức toán]**
>
> $$
> \alpha_{resist} = Am + B
> \tag{5.45}
> $$
>
> trong đó:
>
> $$
> A = (\alpha_{PAC} - \alpha_P)[\text{PAC}]_0
> $$
>
> $$
> B = \alpha_P[\text{PAC}]_0 + \alpha_R[R] + \alpha_S[S]
> $$
>
> $$
> m = \frac{[\text{PAC}]}{[\text{PAC}]_0}
> $$

---

`A` và `B` trong Phương trình `5.45` là các tham số có thể đo được thực nghiệm cho một `photoresist` cụ thể và được gọi là hai tham số Dill đầu tiên `[5.21]`. `A` là hệ số hấp thụ của các thành phần có thể tẩy trắng (`bleachable`) của `resist` và `B` là hệ số hấp thụ của các thành phần không thể tẩy trắng (`non-bleachable`) của `resist`. Chúng ta sẽ mô tả cách các tham số này có thể được đo cho một `resist` cụ thể ngay sau đây. Lưu ý rằng khi `resist` chưa được phơi, `m = 1` và `α_resist = A + B`. Khi `resist` được phơi hoàn toàn, `m = 0` và `α_resist = B`.

Bây giờ chúng ta có thể thay Phương trình `5.45` vào Phương trình `5.40` và biểu diễn cường độ ánh sáng xuyên qua lớp `resist` là

---

> **[Công thức toán]**
>
> $$
> \frac{dI}{dz} = -(Am + B)I
> \tag{5.46}
> $$

---

Thật không may, việc giải phương trình này phức tạp bởi thực tế là `m` là hàm số của thời gian và vị trí, vì vậy Phương trình `5.46` thực sự phải được viết là

---

> **[Công thức toán]**
>
> $$
> \frac{dI}{dz} = -[Am(z,t) + B]\,I
> \tag{5.47}
> $$

---

`m` là phần của thành phần `PAC` trong `resist` chưa được phơi tại thời điểm `t`. Nếu chúng ta lại giả sử động học phản ứng bậc một, thì

---

> **[Công thức toán]**
>
> $$
> \frac{dm}{dt} = -CIm
> \tag{5.48}
> $$

---

Phương trình này phát biểu rằng tốc độ phơi của `PAC` tỷ lệ thuận với nồng độ `PAC` chưa phơi còn lại và với cường độ ánh sáng. Hằng số tỷ lệ là `C`, là tham số `resist` Dill thứ ba.

Các Phương trình `5.47` và `5.48` là các phương trình liên kết phải được giải đồng thời. Phương trình thứ ba phải được đưa vào là Phương trình `5.39`, tính đến bất kỳ mẫu sóng dừng nào trong `resist`. Các bộ mô phỏng hiện sẵn có `[5.3, 5.26, 5.27]` giải hệ phương trình này để tính toán sự tiến triển theo thời gian của quá trình phơi `resist`. Một quy trình lặp được sử dụng về cơ bản hoạt động như sau.

Tại `t = 0`, `m = 1` và mẫu cường độ ánh sáng có thể được tính toán trong `resist` bằng cách sử dụng Phương trình `5.39`. Phân bố cường độ này sau đó được dùng trong Phương trình `5.48` để tính toán sự phơi theo vị trí. Kết quả là `m(x,y,z,t₀)` trong trường hợp ba chiều tổng quát. Kết quả sau đó được dùng trong các Phương trình `5.47` và `5.39` để tính toán cường độ ánh sáng tại `t = 0 + Δt`. Kết quả này lại được dùng trong Phương trình `5.48` để tính toán cường độ ánh sáng mới sau bước thời gian tiếp theo. Thông qua quy trình lặp này, sự tiến triển theo thời gian của quá trình phơi được mô phỏng. Kết quả tổng thể là `aerial image` được tạo ra bởi hệ quang học được chuyển đổi thành một `latent image` `3D` trong `photoresist`. **Hình 5.44** đã trình bày một ví dụ về mô phỏng như vậy, trong đó đầu ra được trình bày ở phần dưới của hình là `[PAC]` theo hàm số vị trí ở cuối quá trình phơi.

Việc tính toán `latent image` trong `resist` đòi hỏi kiến thức về các tham số `resist` Dill `A`, `B` và `C`. Các tham số này có thể được đo thực nghiệm cho một vật liệu `resist` cụ thể như minh họa trong **Hình 5.45**. Trong loạt bài báo kinh điển của họ năm `1975`, Dill và các cộng sự đã chứng minh rằng một phép đo đơn giản về sự truyền ánh sáng phụ thuộc thời gian qua một màng `resist` đang phơi có thể được dùng để trích xuất các tham số `A`, `B` và `C`. Như minh họa trong **Hình 5.45**, ánh sáng tại bước sóng phơi được dùng để chiếu sáng một đế được phủ `resist`. Trong trường hợp đơn giản nhất, một đế trong suốt được chọn có cùng chiết suất như `resist`, để không có sự phản xạ nào tại mặt tiếp xúc `resist`/đế. Một lớp phủ chống phản xạ được dùng ở mặt sau của đế để tránh sự phản xạ tại mặt tiếp xúc đó. Một kết quả đo điển hình được trình bày theo sơ đồ trong **Hình 5.46**. Đối với trường hợp đơn giản này, Dill và cộng sự đã chỉ ra rằng `[5.21]`

---

> **[Công thức toán]**
>
> $$
> A = \frac{1}{D}\ln\!\left(\frac{T_\infty}{T_0}\right)
> \tag{5.49}
> $$
>
> $$
> B = -\frac{1}{D}\ln(T_\infty)
> \tag{5.50}
> $$
>
> $$
> C = \frac{A + B}{A\,T_0(1 - T_0)\,T_{12}}\cdot\left.\frac{dT}{dE}\right|_{E=0}
> \tag{5.51}
> $$
>
> trong đó:
>
> $$
> T_{12} = 1 - \left(\frac{n_{resist} - 1}{n_{resist} + 1}\right)^2
> \tag{5.52}
> $$

---

`T₀` là cường độ ánh sáng truyền qua ở đầu quá trình phơi, `T∞` là cường độ ánh sáng truyền qua ở cuối quá trình phơi, `D` là chiều dày `resist` và `T₁₂` là độ truyền qua qua mặt tiếp xúc không khí/`resist`, với `n_resist` là chiết suất của `resist`. Các phương pháp trích xuất tham số tinh vi hơn có thể được sử dụng nếu tình huống thực nghiệm không lý tưởng như **Hình 5.45** `[5.3, 5.21]`.

---

**Hình 5.45:** Thiết lập thực nghiệm khái niệm để đo các tham số Dill đặc trưng cho một `resist` cụ thể.

---

**Hình 5.46:** Kết quả thực nghiệm điển hình từ một phép đo giống như phép đo được trình bày trong Hình `5.45`.

---

**Hình 5.47** trình bày một mô phỏng bổ sung với cùng cấu trúc như đã dùng trong **Hình 5.44**. Liều phơi trong **Hình 5.47** đã được giảm xuống `10%` của giá trị trước đó để minh họa các hiệu ứng của sự tẩy trắng trong quá trình phơi `resist`. Với chỉ `10%` liều phơi, rõ ràng là các lớp trên cùng của `resist` vẫn được phơi nhưng các vùng sâu hơn chưa nhận được đủ thông lượng photon để phơi hoàn toàn `resist`.

---

**Hình 5.47:** Ví dụ mô phỏng giống như trong **Hình 5.44** ngoại trừ liều phơi đã được giảm xuống `10%` giá trị được dùng trong **Hình 5.44**. Các vùng sâu hơn của `photoresist` không được phơi như các vùng gần bề mặt vì các hiệu ứng của sự tẩy trắng.

---

#### 5.5.3.2 Resist DUV

Các `resist` `DUV` khuếch đại hóa học bao gồm một nhựa polymer (bị chặn để làm cho nó không hòa tan trong dung dịch hiện hình trong trường hợp `resist` dương), một `PAG` và các chất phụ gia khác. Động học của phản ứng phơi được giả sử là bậc một, tức là

---

> **[Công thức toán]**
>
> $$
> \frac{d[\text{PAG}]}{dt} = -CI[\text{PAG}]
> \tag{5.53}
> $$

---

trong đó `[PAG]` là nồng độ `PAG` phụ thuộc thời gian, `I` là cường độ phơi và `C` là tốc độ phơi. Lưu ý sự tương đồng với Phương trình `5.48`. Nếu `I` là hằng số trong quá trình phơi,

---

> **[Công thức toán]**
>
> $$
> [\text{PAG}] = [\text{PAG}]_0\, e^{-CIt}
> \tag{5.54}
> $$

---

Vì nồng độ axit `[H]` thu được trực tiếp từ sự phơi của `PAG`, `[H]` được cho bởi

---

> **[Công thức toán]**
>
> $$
> [H] = [\text{PAG}]_0\!\left(1 - e^{-CIt}\right)
> \tag{5.55}
> $$

---

trong đó nói chung, `[H]` và `I` sẽ là `f(x,y,z)`. Nếu cường độ ánh sáng cũng là hàm số của thời gian, thì một kỹ thuật lặp như được mô tả trong phần trước có thể được dùng để tính toán `H(x,y,z,t)`.

`Aerial image` do đó được chuyển đổi thành một `latent image` `3D` trong `resist` được "lưu trữ" như `H(x, y, z)` ở cuối quá trình phơi. Các kết quả mô phỏng sẽ trông rất giống các ví dụ được trình bày trước đó trong các **Hình 5.44** và **5.47**.

---

### 5.5.4 Nung sau phơi (PEB)

Một khi quá trình phơi `resist` hoàn tất, bước tiếp theo thường là nung nhiệt sau phơi (`PEB`). Trên thực tế, có một số bước nung thường được áp dụng trong xử lý `photoresist` và mỗi bước này có thể có tác động lên mẫu `resist` cuối cùng.

Như đã chỉ ra trong **Hình 5.31**, bước nung đầu tiên thường là bước `prebake` trước khi `resist` được phơi. Bước này được thiết kế để bay hơi hầu hết dung môi còn lại trong `resist`. Tuy nhiên, bước này cũng có thể có tác động lên hóa học `photoresist`. Ở nhiệt độ `prebake` (thường `90 - 100°C`), `PAC` trong các `resist` `DNQ` bắt đầu phân hủy thành một sản phẩm không nhạy quang `[5.30]`. Kết quả định tính của điều này là nồng độ của `PAC` ở đầu quá trình phơi, `[PAC]₀`, nhỏ hơn nồng độ ban đầu trong `resist`. Các điều kiện `prebake` tiêu chuẩn thường dẫn đến `10%` hoặc ít hơn của `PAC` bị phân hủy. Đã có một số công trình về mô hình hóa định lượng các hiệu ứng này `[5.3, 5.31]`, nhưng trong nhiều trường hợp, các tham số `resist` cần thiết cho các mô hình như vậy không được biết rõ và các quá trình hóa học đang diễn ra không được hiểu đầy đủ. Hầu hết các bộ mô phỏng quang khắc hiện sẵn có không mô hình hóa các hiệu ứng của `prebake` của `resist` chút nào, vì vậy chúng ta sẽ không xử lý bước nung cụ thể này thêm nữa.

#### 5.5.4.1 Resist DNQ vạch g và vạch i

Nung sau phơi (`PEB`) đôi khi được đưa vào các `process flow` của `resist` `DNQ` để giảm các hiệu ứng sóng dừng. Chúng ta đã thấy các ví dụ về các hiệu ứng này trong các mô phỏng ở phần trước. Nếu không có biện pháp nào để giảm thiểu các hiệu ứng sóng dừng, ảnh `resist` sau hiện hình sẽ có các cạnh răng cưa rõ rệt (nhớ lại **Hình 5.24**). Điều này nói chung là không mong muốn vì nó làm suy giảm việc kiểm soát chiều rộng vạch và độ phân giải. May mắn thay, người ta đã phát hiện ra rằng một bước nung nhiệt đơn giản giữa phơi và hiện hình có thể có tác động đáng kể đến các hiệu ứng sóng dừng `[5.32]`. Thông thường, bước nung này là `10 - 30 phút` ở khoảng `100°C` (tương tự bước `prebake` của `resist`).

Tác động của nung sau phơi lên hóa học của `resist` `DNQ` thường được mô hình hóa như một quá trình khuếch tán đơn giản. `PAC` đã phơi (`P` theo thuật ngữ của chúng ta) được giả sử có thể khuếch tán trong `resist` với một hệ số khuếch tán được cho bởi

---

> **[Công thức toán]**
>
> $$
> D_P = D_0 \exp\!\left(-E_A / kT\right)
> \tag{5.56}
> $$

---

Biểu thức này có cùng dạng với các hệ số khuếch tán của chất pha tạp mà chúng ta sẽ thảo luận trong Chương `7`. Tác động của sự khuếch tán `PAC` đơn giản là "làm mờ" các hiệu ứng sóng dừng.

Quá trình khuếch tán như vậy có thể được mô hình hóa trong các bộ mô phỏng quang khắc. Tuy nhiên, điều này phức tạp hơn vẻ ngoài thoạt nhìn, thứ nhất vì `D_P` chưa được đo cho hầu hết các `resist`, và thứ hai, vì nhiều khả năng hệ số khuếch tán không đơn giản như Phương trình `5.56` có thể gợi ý. Ví dụ, người ta tin rằng `D_P` phụ thuộc vào nồng độ.

Trong một số bộ mô phỏng quang khắc, các giá trị mặc định hoặc do người dùng chỉ định cho `D_P` được sử dụng cùng với Phương trình `5.56`. Nung sau phơi sau đó được mô hình hóa như một quá trình khuếch tán. Trong các bộ mô phỏng khác, một cách tiếp cận đơn giản hơn được áp dụng do thiếu dữ liệu `D_P`. Các bộ mô phỏng này mô hình hóa nung sau phơi bằng một mô hình độ dài khuếch tán đơn giản. Khoảng cách mà sự "làm mờ" của `PAC` xảy ra trong quá trình nung đơn giản được cho bởi

---

> **[Công thức toán]**
>
> $$
> \sigma = \sqrt{2D_P t_{bake}}
> \tag{5.57}
> $$

---

trong đó `t_bake` là thời gian nung. `σ` có đơn vị độ dài và nói chung là một tham số do người dùng cung cấp trong các bộ mô phỏng. Một giá trị điển hình có thể là `≈ 0,05 µm` (`50 nm`) hay khoảng `λ/4`.

**Hình 5.48** minh họa tác động của nung sau phơi như vậy lên mô phỏng đã trình bày trước đó trong **Hình 5.44**. Sự làm mờ của mẫu sóng dừng rõ ràng trong `[PAC]` được tính toán.

---

**Hình 5.48:** Ví dụ mô phỏng giống như trong **Hình 5.44** ngoại trừ đã bao gồm nung sau phơi `45 phút` ở `115°C`. Các đường đồng mức thang xám lại tương ứng với `[PAC]` sau khi phơi. Lưu ý rằng các hiệu ứng sóng dừng rõ ràng trong **Hình 5.44** đã được "làm mờ" bởi lần nung này, tạo ra phân bố `[PAC]` đồng đều hơn.

---

#### 5.5.4.2 Resist DUV

Trong các `resist` `DUV`, `PEB` là một bước quan trọng vì nó hoàn tất quá trình phơi bằng cách thúc đẩy phản ứng giữa các phân tử `PAG` và các chuỗi polymer. Trong các `resist` `DUV` dương, phản ứng này bỏ chặn chuỗi polymer, làm cho nó hòa tan trong dung dịch hiện hình. Trong các `resist` âm, `PAG` thúc đẩy một phản ứng tạo liên kết ngang (`crosslinking`) làm cho `resist` không hòa tan trong dung dịch hiện hình. Trong cả hai trường hợp, các phân tử axit không bị tiêu thụ bởi các phản ứng và do đó ở bậc thứ nhất, `[H]` được cho bởi Phương trình `5.55` vẫn không đổi trong quá trình `PEB`.

Nếu `[M]` đại diện cho nồng độ của các vị trí phản ứng trên các chuỗi polymer `resist`, thì

---

> **[Công thức toán]**
>
> $$
> \frac{d[M]}{dt} = -C[M][H]
> \tag{5.58}
> $$

---

trong đó `C` là hằng số tốc độ phản ứng. Biểu thức này giả sử rằng phản ứng giữa axit `H` và các vị trí phản ứng `M` là bậc một. Trong quá trình `PEB`, `M` bắt đầu với nồng độ ban đầu `[M₀]` và giảm theo thời gian.

---

> **[Công thức toán]**
>
> $$
> [M_0] - [M] = [M_0]\!\left(1 - e^{-C[H]t}\right)
> \tag{5.59}
> $$

---

Nói chung, `[H]` và do đó `[M]` là `f(x, y, z, t)`.

`PEB` cung cấp năng lượng nhiệt cho phản ứng này diễn ra vì `C` trong Phương trình `5.58` nói chung phụ thuộc theo hàm mũ vào nhiệt độ. Quá trình thứ hai được thúc đẩy bởi nhiệt độ là sự khuếch tán của các phân tử axit, vì chúng phải di chuyển vật lý từ vị trí phản ứng này sang vị trí phản ứng khác để hoàn tất việc phơi `resist` (nhớ lại **Hình 5.19**). Quá trình khuếch tán này được mô tả bởi một phương trình khuếch tán tiêu chuẩn, trong một chiều là

---

> **[Công thức toán]**
>
> $$
> \frac{\partial[H]}{\partial t} = \frac{\partial}{\partial x}\!\left(D_H \frac{\partial[H]}{\partial x}\right)
> \tag{5.60}
> $$

---

Chúng ta sẽ thảo luận về khuếch tán và phương trình này chi tiết hơn nhiều trong Chương `7`.

Hệ số khuếch tán `D_H` của các phân tử axit nói chung phụ thuộc theo hàm mũ vào nhiệt độ như trong Phương trình `5.56`. Nhưng nó cũng có thể phụ thuộc vào nồng độ axit, làm cho bài toán mô hình hóa khó khăn hơn. Do đó, mô phỏng quá trình `PEB` trong một `resist` `DUV` phụ thuộc vào việc giải đồng thời các Phương trình `5.58` và `5.60`, một hệ phương trình được gọi là các phương trình phản ứng-khuếch tán (`reaction-diffusion equations`). Điều này đơn giản để triển khai mặc dù cần có một số tham số bao gồm `D_H`, `M₀`, `C` và dĩ nhiên `H(x, y, z)`. Một phức tạp cuối cùng có thể xuất hiện trong các mô phỏng như vậy là nồng độ axit `[H]` có thể không độc lập với thời gian vì các cơ chế tổn thất khác nhau có thể xảy ra trong quá trình `PEB`. Các cơ chế này bao gồm đầu độc bởi các chất nhiễm bẩn kiềm trong khí quyển, bay hơi của các phân tử axit, hoặc đơn giản là sự bẫy các phân tử axit tại các vị trí trong `photoresist`. Tất cả các cơ chế này có thể được mô hình hóa và đưa vào các mô phỏng nếu có các mô hình và tham số cụ thể. Nói chung, các hiệu ứng như vậy không được đưa vào các bộ mô phỏng ngày nay. Mô phỏng các hiệu ứng `PEB` trên các `resist` `DUV` sẽ trông tương tự như **Hình 5.48**.

---

### 5.5.5 Hiện hình photoresist

Một số mô hình đã được sử dụng để mô tả việc hiện hình `photoresist`. Các mô hình sớm nhất đến từ Dill và các cộng sự và dựa trên cơ sở thực nghiệm `[5.21]`. Một số mô hình gần đây hơn đã cố gắng sử dụng cơ sở vật lý hơn `[5.33]`. Trong tất cả các trường hợp, quá trình về cơ bản được mô tả như một quá trình khắc kiểm soát bề mặt. Dung dịch hiện hình được giả sử khắc bề mặt của `resist` đẳng hướng tại một điểm `(x,y,z)` với tốc độ được xác định bởi nồng độ chất ức chế `resist` tại điểm đó. Hợp chất quang hoạt (`PAC`) trong các `resist` `DNQ` hoặc các polymer bị chặn trong các `resist` `DUV` không hòa tan trong dung dịch hiện hình, trong khi khi `PAC` được chuyển đổi thành axit carboxylic (`P`) trong các `resist` `DNQ`, hoặc khi `PAG` bỏ chặn các chuỗi polymer trong các `resist` `DUV` trong quá trình phơi, `resist` trở nên khá hòa tan trong dung dịch hiện hình. Chúng ta sẽ mô tả quá trình hiện hình dưới đây theo các tham số của `resist` `DNQ`. Tuy nhiên, các mô hình tương tự áp dụng cho các `resist` `DUV`.

Tốc độ hiện hình hay khắc tại điểm `(x,y,z)` do đó phụ thuộc vào `[P]` hay `[PAC]` tại điểm đó. Đây chính xác là điều được tính toán bởi các mô hình phơi mà chúng ta đã mô tả trước đó, và những gì được trình bày trong các ví dụ trong các **Hình 5.44**, **5.47** và **5.48**. Điều cần thiết sau đó là một mối quan hệ toán học giữa `[P]` hay `[PAC]` và tốc độ hiện hình.

Mối quan hệ đầu tiên như vậy được mô tả bởi Dill và cộng sự `[5.21]` và được triển khai trong các bộ mô phỏng ngày nay thường ở dạng như sau `[5.26]`

---

> **[Công thức toán]**
>
> $$
> R(x,y,z) =
> \begin{cases}
> 0.006\exp(E_1 + E_2 m + E_3 m^2)
> & \text{nếu } m > -\dfrac{E_2}{2E_3} \\[8pt]
> 0.006\exp\!\left(E_1 + \dfrac{E_2 - E_3(E_2 - 1)}{1}\right)
> & \text{trường hợp còn lại}
> \end{cases}
> \tag{5.61}
> $$

---

`R(x,y,z)` là tốc độ hiện hình hay khắc cục bộ tính theo `µm min⁻¹`, `m` (thực ra là `m(x,y,z)`) đã được định nghĩa trong Phương trình `5.45` và là `[PAC]` cục bộ sau khi phơi, và `E₁`, `E₂` và `E₃` là các tham số thực nghiệm thu được từ việc khớp Phương trình `5.61` với dữ liệu thực nghiệm.

Một mô hình có cơ sở vật lý hơn cho việc hiện hình `resist` đã được Mack đề xuất `[5.33]`. Mô hình này có nhiều điểm tương đồng với mô hình oxy hóa Deal-Grove mà chúng ta sẽ thảo luận trong Chương `6`. Mô hình của Mack được minh họa trong **Hình 5.48** *(chú ý: trong bản gốc hình này được đánh số 5.48 nhưng có thể là 5.49 theo thứ tự)*. Trong mô hình này, ba thông lượng được dùng để mô tả quá trình hiện hình. `F₁` đại diện cho sự khuếch tán của dung dịch hiện hình từ khối chất lỏng tới bề mặt `resist`. `F₂` đại diện cho phản ứng của dung dịch hiện hình với `resist` và `F₃` đại diện cho sự khuếch tán của các sản phẩm phản ứng trở lại vào dung dịch hiện hình. `F₃` được giả sử là rất nhanh (không giới hạn tốc độ) và do đó bị bỏ qua trong phân tích của Mack.

---

**Hình 5.48:** Mô hình của Mack cho việc hiện hình `photoresist`.

---

`F₁` được giả sử được thúc đẩy bởi gradient nồng độ giữa dung dịch hiện hình lỏng và bề mặt `resist` và được cho bởi

---

> **[Công thức toán]**
>
> $$
> F_1 = k_D(C_D - C_S)
> \tag{5.62}
> $$

---

trong đó `k_D` là hệ số truyền khối (`mass transfer coefficient`) gắn với sự khuếch tán của dung dịch hiện hình (`cm s⁻¹`), `C_D` là nồng độ dung dịch hiện hình khối và `C_S` là nồng độ dung dịch hiện hình tại bề mặt `resist`. `F₂` được giả sử phụ thuộc vào nồng độ của hai chất phản ứng tại bề mặt `resist` và được cho bởi

---

> **[Công thức toán]**
>
> $$
> F_2 = k_R C_S [P]^n
> \tag{5.63}
> $$

---

trong đó `k_R` là hằng số tốc độ gắn với phản ứng dung dịch hiện hình-`resist` (`cm s⁻¹`) và `[P]` là nồng độ cục bộ của `PAC` đã phản ứng như đã định nghĩa trước đó. Ở đây, người ta giả sử rằng phản ứng tỷ lệ với lũy thừa nào đó của `[P]`, tức là một số `n` phân tử sản phẩm `P` phản ứng với dung dịch hiện hình để hòa tan một phân tử nhựa trong `resist`.

`F₁` và `F₂` nối tiếp nhau và do đó chúng ta đặt `F₁ = F₂` ở trạng thái dừng. Do đó

---

> **[Công thức toán]**
>
> $$
> F_1 = F_2 = \frac{k_D k_R C_D [P]^n}{k_D + k_R [P]^n}
> \tag{5.64}
> $$

---

Nhớ lại định nghĩa của `[P]` và `m` trong các Phương trình `5.44` và `5.45`, cuối cùng chúng ta có tốc độ hiện hình `r = F₁ = F₂` là

---

> **[Công thức toán]**
>
> $$
> r = \frac{k_D C_D (1-m)^n}{\dfrac{k_D}{k_R [\text{PAC}]_0^n} + (1-m)^n}
> \tag{5.65}
> $$

---

Khi `m = 1`, `resist` chưa được phơi và `r → 0`. Điều này không đúng về mặt vật lý vì các `resist` `DNQ` thông thường hòa tan trong dung dịch hiện hình ở tốc độ khác không ngay cả khi chúng chưa được phơi. Phương trình `5.65` có thể được hiệu chỉnh để tính đến điều này như sau:

---

> **[Công thức toán]**
>
> $$
> r = \frac{k_D C_D (1-m)^n}{\dfrac{k_D}{k_R [\text{PAC}]_0^n} + (1-m)^n} + r_{min}
> \tag{5.66}
> $$

---

trong đó `r_min` là tốc độ hòa tan trong `resist` chưa phơi. Khi `m = 0`, `resist` được phơi hoàn toàn và `r → r_max`, trong đó

---

> **[Công thức toán]**
>
> $$
> r_{max} = \frac{k_D C_D}{\dfrac{k_D}{k_R [\text{PAC}]_0^n} + 1} + r_{min}
> \tag{5.67}
> $$

---

Chúng ta có thể xem xét hai trường hợp giới hạn của mô hình này. Nếu quá trình khuếch tán trong dung dịch hiện hình lỏng là nhanh, phản ứng tổng thể sẽ bị giới hạn bởi phản ứng tại bề mặt (giới hạn bởi tốc độ phản ứng bề mặt). Mặt khác, nếu tốc độ phản ứng bề mặt nhanh hơn, phản ứng tổng thể sẽ "bị giới hạn bởi khuếch tán".

---

> **[Công thức toán]**
>
> $$
> r \approx
> \begin{cases}
> k_R C_D [P]^n + r_{min} & \text{giới hạn tốc độ phản ứng bề mặt} \\
> k_D C_D + r_{min} & \text{giới hạn tốc độ khuếch tán}
> \end{cases}
> \tag{5.68}
> $$

---

Phương trình `5.66` thường được viết theo dạng sau:

---

> **[Công thức toán]**
>
> $$
> r = r_{max}\frac{(a+1)(1-m)^n}{a + (1-m)^n} + r_{min}
> \tag{5.69}
> $$
>
> trong đó:
>
> $$
> a = \frac{k_D}{k_R [\text{PAC}]_0^n}
> \tag{5.70}
> $$

---

Tham số `a` thực sự là thước đo tỷ lệ tương đối giữa khuếch tán và phản ứng bề mặt.

Để sử dụng mô hình này, có bốn tham số phải được xác định thực nghiệm: `a`, `n`, `r_max` và `r_min`, mặc dù `r_min` thường là không đáng kể và do đó có thể chỉ có ba tham số. Mô hình gốc của Dill cũng chứa ba tham số. Tuy nhiên, mô hình của Mack cố gắng sử dụng các tham số có cơ sở vật lý nào đó trái ngược với các tham số thuần thực nghiệm trong mô hình của Dill.

Các bộ mô phỏng thương mại sẵn có nói chung triển khai một số mô hình hiện hình `resist`, bao gồm hai mô hình được mô tả ở đây. Sự tiến triển theo thời gian của biên dạng `resist` đang hiện hình được tính toán bằng cách thiết lập một lưới hai hoặc ba chiều, trong đó mỗi điểm lưới trong `resist` có một giá trị cụ thể của `m(x,y,z)`. Mẫu hiện hình sau đó được phép tiến triển theo thời gian với dung dịch hiện hình di chuyển vào trong `resist` ở tốc độ cục bộ được xác định bởi mô hình hiện hình.

**Hình 5.50** trình bày một ví dụ về mô phỏng của quá trình hiện hình. Trong ví dụ này, mô hình hiện hình đơn giản nhất (mô hình Dill) được sử dụng. Các tham số bình thường được sử dụng trong mô phỏng cho thời gian phơi và thời gian hiện hình, và nung sau phơi được đưa vào để giảm thiểu các hiệu ứng sóng dừng. Mẫu `resist` đã hiện hình thu được cho thấy độ phân giải tốt và các vách bên (`sidewalls`) khá sắc nét. Mô phỏng ở dưới bên trái cho thấy biên dạng `resist` giữa chừng quá trình hiện hình. Lưu ý cách hình dạng của `resist` còn lại tại điểm này phản ánh nồng độ `PAC` trong mẫu `resist`.

---

**Hình 5.50:** Ví dụ về tính toán một lớp `photoresist` đã hiện hình sử dụng bộ mô phỏng `ATHENA` của Silvaco. `Resist` được phơi với liều `200 mJ cm⁻²`, nung sau phơi `45 phút` ở `115°C` được sử dụng, và mẫu được hiện hình trong `60 giây`, tất cả đều là các tham số bình thường. Mô hình hiện hình Dill được sử dụng. Ảnh trên cùng trình bày nồng độ `PAC` sau khi phơi và nung sau phơi. Các mô phỏng ở dưới cho thấy biên dạng `resist` đã hiện hình giữa chừng quá trình hiện hình (trái) và sau khi hiện hình hoàn tất (phải). Mẫu `resist` được xác định rõ ràng trong mô phỏng này.

---

### 5.5.6 Nung sau của photoresist

Như trình bày trong **Hình 5.31**, bước cuối cùng trong một quy trình `photoresist` điển hình là `postbake`, thường được thực hiện ở `100 - 140°C` trong `10 - 30 phút`. Bước này làm cứng `resist` bằng cách bay hơi bất kỳ dung môi còn lại nào và cũng cải thiện sự bám dính với các vật liệu bên dưới. Vì `resist` nói chung được dùng để che chắn một bước khắc plasma, hoặc để chặn một bước cấy ion, quá trình làm cứng này quan trọng trong việc cải thiện độ bền của `resist`. `Resist` nói chung sẽ chảy phần nào trong quá trình `postbake` này, làm bo tròn các cạnh của biên dạng. Rõ ràng mức độ chảy phụ thuộc vào thời gian và nhiệt độ của `postbake`, cũng như vào các tính chất vật liệu của `resist`.

Hầu hết các bộ mô phỏng quang khắc không mô hình hóa quá trình `postbake` này. Tuy nhiên, một số công cụ này đã triển khai một bộ mô phỏng chảy (`flow simulator`) sử dụng các mô hình tương tự như các mô hình tái chảy kính (`glass reflow`) được thảo luận trong Chương `11`. Một thảo luận chi tiết về các mô hình như vậy được đưa vào Chương `11`, vì vậy sẽ không được lặp lại ở đây. **Hình 5.51** trình bày một ví dụ về các hiệu ứng được mô phỏng của `postbake` lên biên dạng `resist`.

---

**Hình 5.51:** Ví dụ về mô phỏng quá trình tái chảy sử dụng bộ mô phỏng `ATHENA` của Silvaco. Mẫu `resist` đã hiện hình ban đầu được trình bày ở bên trái. Nung `10 phút` ở `130°C` dẫn đến cấu trúc ở bên phải. Lưu ý các hiệu ứng sóng dừng hiện diện trong biên dạng `resist` đã hiện hình, biến mất sau khi tái chảy.

---

### 5.5.7 Kỹ thuật thiết kế mask nâng cao

Trong Mục `5.2.4`, chúng ta đã mô tả một số khái niệm kỹ thuật thiết kế `mask` nâng cao đang được áp dụng cho các `mask` để cải thiện độ phân giải của các hệ thống chiếu ảnh quang học. Các phương pháp này bao gồm hiệu chỉnh lân cận quang học (`OPC`) và các `mask` dịch pha (`phase shift masks`). Các kỹ thuật này về cơ bản thay đổi mô tả của hàm truyền qua của `mask` (Phương trình `5.21`). Các bộ mô phỏng hiện đại bao gồm các khả năng này đơn giản bằng cách thay đổi mô tả `mask` trong đầu vào của bộ mô phỏng. Một ví dụ về mô phỏng như vậy được trình bày trong **Hình 5.52**, trong đó một lỗ tiếp xúc (`contact hole`) nhỏ được in trong `resist` sử dụng một `mask` có và không có dịch pha. Chất lượng cao hơn của ảnh đã hiện hình trong `resist` rõ ràng trong trường hợp với `mask` dịch pha.

Các công cụ mô phỏng nhiều khả năng sẽ đóng vai trò ngày càng quan trọng hơn khi nhiều thiết kế `mask` hơn kết hợp các đặc tính nâng cao này. Việc thiết kế các mẫu `mask` như vậy không đơn giản và việc sử dụng máy tính để vừa hỗ trợ thiết kế vừa "kiểm tra" thiết kế bằng cách sử dụng các công cụ mô phỏng nhiều khả năng sẽ trở nên rất phổ biến trong tương lai.

---

**Hình 5.52:** Ví dụ về mô phỏng một ảnh `photoresist` đã hiện hình với một `mask` dịch pha sử dụng bộ mô phỏng `ATHENA` của Silvaco. Trong ví dụ trên, thiết kế `mask` ở bên trái là một lỗ tiếp xúc `0,3 µm` (vùng trung tâm) với các đặc trưng dịch pha `0,1 µm` ở ngoài đường viền của lỗ tiếp xúc ("outriggers"). Các đặc trưng này vắng mặt trong ví dụ ở dưới. Sự khác biệt trong các đặc trưng lỗ tiếp xúc đã hiện hình là rõ ràng. Trong trường hợp này, một `stepper` vạch `i` với `NA = 0,54` được sử dụng trong mô phỏng cùng với các chu kỳ nung sau phơi và hiện hình bình thường.

## 5.6 Các giới hạn và xu hướng tương lai trong công nghệ và mô hình

Sự tàn lụi của quang khắc quang học đã được dự đoán nhiều lần trong thập kỷ qua. Tuy nhiên, các cải tiến liên tục trong các hệ thống phơi chiếu quang học vẫn theo kịp các nhu cầu sản xuất. `SIA NTRS` được mô tả ở đầu chương này dự đoán nhu cầu về các đặc trưng `0,18 µm` vào năm `1999`, `0,13 µm` vào năm `2003` và `0,1 µm` vào năm `2006`. Hiện nay có vẻ khả năng là các hệ thống phơi chiếu quang học có thể cung cấp các công cụ cần thiết cho các thế hệ `0,18` và `0,13 µm` và có lẽ cả thế hệ `0,1 µm`, sử dụng các nguồn laser excimer `193 nm` và các hệ thống `step and scan`. Thậm chí hiện nay cũng có một số nghiên cứu về nguồn laser excimer `157 nm` (`F₂`). Tuy nhiên, ở đâu đó sau thế hệ `0,1 µm`, sự tàn lụi thực sự của quang khắc quang học có lẽ sẽ xảy ra. Các giới hạn nhiễu xạ sẽ đòi hỏi các nguồn bước sóng ngắn hơn nhiều, và các hệ thống phơi chiếu nhiều khả năng sẽ không sử dụng quang học khúc xạ vì khó khăn trong việc tìm kiếm các vật liệu trong suốt ở các bước sóng ngắn hơn này.

Không có sự đồng thuận về các cách tiếp cận quang khắc cho việc chế tạo các mạch tích hợp có đặc trưng `< 0,1 µm`. Rõ ràng là hiện đang có một lượng nghiên cứu đáng kể để đánh giá các lựa chọn thay thế khác nhau, vì nếu không tìm được giải pháp, vấn đề này sẽ là rào cản ngăn chặn (`showstopper`) cho sự tiến hóa tiếp tục của `IC`. Chúng ta sẽ đề cập ngắn gọn ở đây một số lựa chọn thay thế đáng kể cho quang khắc trong thế kỷ tới.

---

### 5.6.1 Quang khắc chùm điện tử

Các hệ thống chùm điện tử đã được sử dụng trong nhiều năm để chế tạo các `mask` cần thiết cho quang khắc quang học, như đã minh họa trong **Hình 5.1**. Không có lý do khái niệm nào tại sao một hệ thống như vậy không thể được sử dụng để ghi trực tiếp các mẫu vào `photoresist` trên các wafer thay vì vào `photoresist` trên các đế `mask`. Trên thực tế, trong nhiều năm, kỹ thuật này đã là phương pháp được lựa chọn cho nghiên cứu linh kiện tiên tiến vì độ phân giải tuyệt vời được cung cấp bởi các công cụ `e-beam`. Mặc dù các electron có các tính chất sóng, bước sóng của các electron được sử dụng trong các công cụ phơi chiếu này nhỏ hơn `0,1 nm`, vì vậy các hiệu ứng nhiễu xạ và các giới hạn mà chúng áp đặt lên các hệ thống phơi chiếu quang học không phải là vấn đề trong các hệ thống `e-beam`. Ngay cả `20` năm trước, các kích thước đặc trưng nhỏ hơn `10 nm` đã được chứng minh `[5.34]`. Do đó không có câu hỏi nào về khả năng của các công cụ `e-beam` trong việc cung cấp độ phân giải cần thiết cho các kích thước đặc trưng qua đến cuối `SIA NTRS` hiện tại.

Nhược điểm chính của các công cụ `e-beam` là thông lượng rất nhỏ so với các `stepper` quang học hiện tại. Các công cụ `e-beam` đơn giản nhất về cơ bản phơi `resist` từng pixel một, một quá trình nối tiếp. Ngược lại, các `stepper` quang học phơi các pixel trên một vùng của wafer song song nhau. Đây là sự khác biệt lớn và dẫn đến việc các công cụ quang khắc `e-beam` có thông lượng vào cỡ một wafer mỗi giờ so với `> 50` wafer mỗi giờ đối với các `stepper` quang học hiện đại. Sự khác biệt về chi phí sản xuất gắn với hai công nghệ này là như vậy nên đến nay các công cụ `e-beam` chưa tìm thấy ứng dụng trong các nhà máy sản xuất chủ đạo. Các công cụ `e-beam` ngày nay được sử dụng để chế tạo số lượng nhỏ các linh kiện và mạch thử nghiệm, và cho việc sản xuất quy mô nhỏ của các chip mục đích đặc biệt, đòi hỏi các đặc trưng nhỏ hoặc thời gian xử lý nhanh. (Vì không cần phải chế tạo `mask`, thời gian cần để đi từ thiết kế đến một chip được chế tạo có thể ngắn hơn khi sử dụng quang khắc `e-beam`, mặc dù chỉ cho số lượng nhỏ chip.)

Giới hạn thông lượng đối với các hệ thống `e-beam` phát sinh từ một số cân nhắc. Thứ nhất, nguồn điện tử chỉ có thể cung cấp một mật độ dòng hữu hạn. Vì cần có số lượng electron tối thiểu để phơi mỗi pixel trong `resist`, điều này đặt ra một giới hạn trên cho tốc độ có thể quét chùm tia trên wafer. Nếu độ nhạy của `resist` là `S`, thì số lượng electron tối thiểu cần thiết để phơi mỗi pixel đơn giản là

---

> **[Công thức toán]**
>
> $$
> N = \frac{S\, I_P^2}{q}
> \tag{5.71}
> $$

---

trong đó `I_P` là kích thước pixel. Thứ hai, ở cường độ chùm tia cao, độ phân giải có thể bị suy giảm do mất tiêu cự gây ra bởi lực đẩy Coulomb của các electron tích điện trong chùm tia. Các cách tiếp cận để vượt qua các giới hạn này bao gồm sử dụng nhiều nguồn điện tử để có thể thực hiện việc ghi song song, định hình chùm tia thành các hình chữ nhật đủ lớn để phơi các đặc trưng đầy đủ trên wafer thay vì các pixel riêng lẻ, cải thiện độ nhạy của các `resist` `e-beam`, và sử dụng quang khắc chiếu ảnh `e-beam` trong đó một `mask` khuôn tô (`stencil mask`) chứa các mẫu phức tạp được hội tụ lên wafer. Cách tiếp cận sau này hữu ích nhất khi `IC` chứa các mẫu lặp lại, chẳng hạn như trong các chip bộ nhớ.

Các hiệu ứng lân cận (`proximity effects`) là một vấn đề đáng kể bổ sung gắn với việc ghi trực tiếp bằng `e-beam`. Các electron tác động lên `resist` thường có năng lượng `10 - 20 keV` và truyền khoảng cách lớn hơn một micron trước khi dừng lại. Chúng truyền năng lượng cho các vật liệu `resist` và đế qua nhiều tương tác khác nhau bao gồm tán xạ đàn hồi từ các hạt nhân và các tương tác không đàn hồi như được minh họa trong **Hình 4.18**. Trên thực tế, quá trình dừng tổng thể không khác với quá trình cấy ion được mô tả chi tiết trong Chương `8`. Vì các electron có tầm hoạt động rất dài và vì chúng tán xạ rất dễ dàng, sự phơi của các vùng lân cận với các vùng phơi mong muốn thực sự có xảy ra. Điều này được gọi là hiệu ứng lân cận. Có thể mô hình hóa hiệu ứng này vì toàn bộ mẫu `mask` được biết và hiệu chỉnh quá trình phơi cho hiệu ứng này. Quy trình về cơ bản là tính toán lượng phơi xảy ra ở các vùng lân cận do tán xạ, và sau đó điều chỉnh liều điện tử theo không gian để bù đắp cho các hiệu ứng như vậy. Các thuật toán tinh vi đã được phát triển để thực hiện điều này `[5.35]`.

Có lẽ cách tiếp cận đầy hứa hẹn nhất cho quang khắc `e-beam` thông lượng cao là `SCALPEL®` (`SCattering with Angular Limitation Projection Electron-beam Lithography`), được phát minh tại Bell Laboratories năm `1989` `[5.36]`. Phát minh này được thúc đẩy bởi hai quan sát về các hệ thống chiếu ảnh `e-beam`. Quan sát thứ nhất là các hệ thống `mask` khuôn tô hiện có, về cơ bản hấp thụ chùm điện tử trong các phần của `mask` dự định là bất trong suốt, bị các vấn đề gia nhiệt do năng lượng hấp thụ từ chùm `e-beam`. Điều này giới hạn điện áp gia tốc có thể được sử dụng trong các hệ thống này. Quan sát thứ hai là các hệ thống quang học điện tử trường đầy đủ đòi hỏi các khẩu độ số nhỏ khi kích thước die tăng và kích thước đặc trưng giảm. Kết quả là, các mật độ dòng chùm tia cần thiết cho thông lượng hợp lý trong các hệ thống này dẫn đến các hiệu ứng điện tích không gian (`space-charge effects`) đáng kể làm phá hủy độ phân giải của hệ thống. Giải pháp cho các vấn đề này được đề xuất trong hệ thống `SCALPEL®` về cơ bản liên quan đến một thiết kế `mask` mới. Nguyên lý được minh họa trong **Hình 5.53**.

---

**Hình 5.53:** Hệ thống quang khắc chiếu ảnh `e-beam` `SCALPEL®`. `Resist` được "phơi" ở các vùng mà chùm `e-beam` không bị tán xạ rộng (các vùng `mask` không có chất tán xạ). Khi chùm `e-beam` bị tán xạ rộng, cường độ tới `resist` không đủ để phơi.

---

`Mask` bao gồm một màng số nguyên tử thấp (thường là `Si₃N₄`) và một mẫu số nguyên tử cao mỏng (thường là vài chục `nm` của `Cr` hoặc `W`). Cả hai vùng đều về cơ bản trong suốt đối với chùm điện tử `100 keV` chuẩn trực, không kết hợp được sử dụng trong hệ thống. Tuy nhiên, các electron tương tác khác nhau với hai vùng `mask`. Trong các vùng màng, các electron chỉ bị tán xạ yếu đến các góc nhỏ. Trong các vùng `Cr/W`, các electron bị tán xạ mạnh đến các góc lớn. Một hệ thấu kính điện tử hội tụ các electron bị tán xạ lên wafer. Tuy nhiên, một khẩu độ trong mặt phẳng tiêu cự phía sau (`back focal plane`) của hệ thống chiếu ảnh chặn các electron bị tán xạ mạnh. Do đó, một ảnh có độ tương phản cao và độ phân giải cao được tạo ra trên wafer. Khái niệm này đã được chứng minh thực nghiệm và có cả độ phân giải lẫn thông lượng tiềm năng để đáp ứng các yêu cầu của `SIA NTRS` qua tất cả các thế hệ công nghệ hiện có trong lộ trình `[5.37]`. Hệ thống thu nhỏ ảnh `mask` thường `4:1`, không yêu cầu mẫu `mask` ngoại lai (`OPC` hay `phase shift masks`), sử dụng cách tiếp cận `step and scan` rất giống với các hệ thống phơi chiếu quang học hiện đại, đạt được độ sâu tiêu cự lớn, và hoạt động với các `resist` `DUV` khuếch đại hóa học tương tự hiện đang được sử dụng cho quang khắc `248 nm`. Cách tiếp cận này chưa được chứng minh trong môi trường sản xuất quy mô đầy đủ, nhưng dường như có triển vọng đáng kể cho các nhu cầu quang khắc tương lai.

---

### 5.6.2 Quang khắc tia X

Các hệ thống quang khắc tia X sử dụng tia X (photon) với năng lượng trong vùng `1 - 10 keV`, tương ứng với các bước sóng vào cỡ `1 nm`. Do đó, các hiệu ứng nhiễu xạ là không đáng kể như trong trường hợp quang khắc `e-beam`. Việc hội tụ tia X là một vấn đề rất khó khăn vì vậy các hệ thống tia X ngày nay nói chung là các hệ thống in tiếp cận (`proximity printing`). Chúng có cấu hình cơ bản minh họa trong **Hình 5.3** ngoại trừ nguồn tia X được sử dụng thay vì nguồn quang học. Hệ thống thường hoạt động trong môi trường chân không, mặc dù bản thân wafer thường ở trong môi trường không khí. Các tia X ra khỏi thiết bị phơi chiếu qua một cửa sổ `Be` mỏng.

Thảo luận về nhiễu xạ trường gần (Fresnel) trước đó trong Chương (Mục `5.2.2.3`) gợi ý rằng độ phân giải rất tốt có thể đạt được với một hệ thống hoạt động ở bước sóng phơi khoảng `1 nm`. Điều này thực sự đúng với các hệ thống tia X. Một số hệ thống như vậy đang được sử dụng ngày nay trong các phòng thí nghiệm nghiên cứu và chúng đã đạt được kích thước đặc trưng `< 0,1 µm`. Các hệ thống này cũng có thông lượng tương đương với các hệ thống phơi chiếu quang học vì chúng phơi một vùng đáng kể trên wafer trong mỗi lần phơi. Các hệ thống thường sử dụng cách tiếp cận `step and repeat` giống như các `stepper` quang học vì các giới hạn trong việc chế tạo các `mask` tia X `1:1` diện tích lớn.

Các vấn đề chính hạn chế việc áp dụng các hệ thống tia X trong sản xuất liên quan đến các `mask` và nguồn tia X. Các vùng "trong suốt" trên `mask` phải trong suốt với tia X `1 nm` và các vùng "tối" phải chặn chúng. Không có vật liệu nào truyền tia X dễ dàng, vì vậy các vùng trong suốt cần được làm từ các lớp mỏng của các vật liệu khối lượng thấp. `Si`, `Si₃N₄`, `SiC` và `BN` dày vài micron là các lựa chọn phổ biến. Các vùng tối cần được làm từ các vật liệu như `Au` hoặc `W` hấp thụ tia X, với `W` có khả năng là lựa chọn chi phối trong tương lai vì các lo ngại về nhiễm bẩn `Au` trong các cơ sở chế tạo. Do đó, một cấu trúc `mask` điển hình là một màng `Si₃N₄` mỏng với một màng `Au` hoặc `W` được lắng đọng và khắc để định nghĩa mẫu `mask`. Một `mask` như vậy rất mỏng manh về mặt cơ học và đòi hỏi việc chế tạo rất cẩn thận để kiểm soát các ứng suất trong màng mỏng. Việc ghi thực tế mẫu trên `mask` tia X thường được thực hiện bằng `photoresist` phủ quay lên chất hấp thụ `Au` hoặc `W` và quang khắc `e-beam` ghi trực tiếp.

Có một số lựa chọn cho các nguồn tia X. Cách tiếp cận đơn giản nhất là bắn phá một mục tiêu kim loại với các electron năng lượng cao. Các electron tới kích thích các electron mức lõi trong mục tiêu, các electron này phát ra tia X khi chúng trở về trạng thái bình thường. (Nhớ lại **Hình 4.17**.) Bước sóng của các photon tia X phát ra đặc trưng cho vật liệu mục tiêu. Cường độ của các nguồn này có thể được tăng lên bằng cách làm mát bằng nước và xoay mục tiêu. Cũng có thể sử dụng các nguồn plasma được gia nhiệt bằng laser. Trong các nguồn này, một xung laser mạnh được áp dụng lên một màng kim loại mỏng, gây ra sự bốc hơi của kim loại. Năng lượng đủ cao để hơi kim loại siêu nhiệt bức xạ tia X với bước sóng `0,5 - 2 nm`. Các nguồn tia X mạnh nhất là các vòng lưu trữ `synchrotron`. Trong các hệ thống này, các electron được lưu hành quanh một vòng ở các năng lượng `10⁶ - 10⁹ eV`. Tại mỗi nam châm uốn (`bending magnet`) quanh một vòng như vậy, một chùm tia X mạnh được phát ra, mỗi chùm phù hợp làm nguồn cho một hệ thống phơi chiếu tia X. Do đó, một vòng lưu trữ có thể hỗ trợ nhiều máy căn chỉnh. Một số vòng như vậy đã được xây dựng trong những năm gần đây cho nghiên cứu quang khắc và các `IC` đã được chế tạo với chúng. Nhược điểm chính của các vòng lưu trữ `synchrotron` là chi phí rất cao. Tuy nhiên, bất kỳ cách tiếp cận quang khắc nào cho các kích thước đặc trưng `< 0,1 µm` đều có khả năng sẽ rất đắt tiền và các nguồn `synchrotron` là lựa chọn có khả năng nhất nếu các hệ thống tia X được sử dụng rộng rãi trong tương lai. **Hình 5.54** minh họa một hệ thống tia X tiếp cận hiện đại với nguồn `synchrotron`.

---

**Hình 5.54:** Hệ thống phơi chiếu tia X tiếp cận. Hình này được lấy từ trang web của Sematech tại `http://www.sematech.org/public/general/annrpt/litho2.htm`.

---

Một lĩnh vực nghiên cứu hiện tại khác liên quan đến các thấu kính và gương để phản xạ và hội tụ tia X. Hầu hết các thấu kính như vậy sử dụng phản xạ từ các gương chiếu xiên (`glancing incidence mirrors`) hoặc các gương đa lớp với chiều dày lớp được thiết kế để sử dụng các hiệu ứng giao thoa tương hỗ xây dựng. Nếu các thấu kính như vậy có thể được phát triển đủ, chúng hứa hẹn chế tạo các `mask` tia X trên các đế phản xạ, một phát triển sẽ có tác động đáng kể đến tiềm năng cho các hệ thống phơi chiếu tia X. Cách tiếp cận đầy hứa hẹn nhất cho các gương tia X sử dụng khái niệm minh họa trong **Hình 5.55**.

Các gương này sử dụng các lớp xen kẽ của hai vật liệu có nồng độ electron rất khác nhau (thường là `Mo` và `Si`). Lớp khối lượng cao đóng vai trò chất tán xạ và lớp khối lượng thấp đóng vai trò chất đệm (`spacer`). Các chiều dày được chọn để giao thoa tương hỗ xây dựng xảy ra giữa các sóng phản xạ một phần tại mỗi lớp. Các gương này ban đầu được phát triển cho thiên văn tia X `[5.38]` và trong những năm gần đây đã đạt được độ phản xạ trên `60%`. Chúng đòi hỏi các dung sai chế tạo phi thường về chiều dày lớp (thường `0,1 nm`) vì các bước sóng ngắn mà các gương được thiết kế để phản xạ. Nếu các gương như vậy có thể được phát triển cho các ứng dụng quang khắc, các thiết kế đã được đề xuất cho các hệ thống phơi chiếu hoàn chỉnh sử dụng chúng cho cả `mask` lẫn quang học thu nhỏ `[5.39]`. Trong trường hợp sau, các gương sẽ phải được xây dựng trên các bề mặt cong. Các hệ thống như vậy đã được gọi là các hệ thống quang khắc `EUV` hay tử ngoại cực hạn. **Hình 5.56** minh họa về mặt khái niệm một hệ thống quang khắc `EUV` có thể trông như thế nào.

---

**Hình 5.55:** Gương đa lớp phù hợp cho phản xạ tia X.

---

**Hình 5.56:** Bản vẽ khái niệm về một hệ thống tạo ảnh `EUV`. Các gương thu nhỏ ảnh chiếu khoảng `4X`. Hình này được lấy trực tiếp từ trang web của Sematech tại `http://www.sematech.org/public/general/annrpt/litho2.htm`.

---

Khả năng thông lượng và độ phân giải tiềm năng của các hệ thống quang khắc tia X nhiều khả năng sẽ thúc đẩy nghiên cứu tiếp tục về các hệ thống này. Nếu các vấn đề `mask` có thể được giải quyết cho các hệ thống tiếp cận hay `EUV`, các hệ thống như vậy có thể cung cấp một lựa chọn sản xuất khả thi cho các đặc trưng `< 0,1 µm`.

---

### 5.6.3 Kỹ thuật thiết kế mask nâng cao

Các nỗ lực tiếp tục cải thiện độ phân giải của các hệ thống quang khắc phải tập trung vào toàn bộ hệ thống, không chỉ thiết bị phơi chiếu. Các cách tiếp cận mạnh mẽ để thiết kế các `mask` với mẫu tinh vi hơn so với đơn giản là một biểu diễn nhị phân chính xác của mẫu mong muốn, đang bắt đầu được sử dụng. Các phương pháp này bao gồm hiệu chỉnh lân cận quang học (`OPC`) và `phase shift masks`. Có khả năng các phương pháp này sẽ được sử dụng rộng rãi hơn trong tương lai. Các rào cản chính đối với việc sử dụng rộng rãi hơn bao gồm các công cụ phần mềm tinh vi cần thiết để hỗ trợ trong việc thiết kế các `mask` như vậy, và dĩ nhiên, chi phí cao hơn của bản thân việc chế tạo `mask`. Vì nhiều kỹ thuật trong số này liên quan đến việc đặt các đặc trưng trên `mask` nhỏ hơn kích thước đặc trưng tối thiểu, việc kiểm tra `mask` và phát hiện khuyết tật cũng khó khăn hơn với các `mask` như vậy. Tuy nhiên, các phương pháp này cung cấp sự cải thiện đáng kể về độ phân giải và do đó động lực để sử dụng chúng là mạnh mẽ.

Nhiều sự thay thế được đề xuất cho quang khắc quang học đòi hỏi sự đổi mới hay phát minh trong các `mask` được sử dụng với thiết bị phơi chiếu. Có khả năng các vấn đề này sẽ có tác động đáng kể đến việc hệ thống phơi chiếu sau quang học nào thực sự đạt đến độ chín về mặt sản xuất.

---

### 5.6.4 Các resist mới

Các `resist` `DNQ` vốn là nền tảng của ngành công nghiệp bán dẫn trong nhiều năm, hiện đang được thay thế bởi các vật liệu mới và hóa học mới phù hợp hơn cho các hệ thống phơi chiếu `DUV`. Nhựa cơ bản (`novolac`) trong các `resist` `DNQ` bắt đầu hấp thụ mạnh bức xạ `UV` ở các bước sóng dưới `250 nm`. Do đó, các `resist` này không thể được sử dụng cho các hệ thống phơi chiếu dựa trên laser excimer `KrF` `248 nm` hoặc `ArF` `193 nm`.

Khái niệm khuếch đại hóa học đã được chứng minh là một ý tưởng mạnh mẽ cho các `resist` mới và nhiều vật liệu mới đã được phát triển trong những năm gần đây. Các `resist` kiểu này hiện đang được sử dụng trong sản xuất ở thế hệ công nghệ `0,25 µm` và nhiều khả năng sẽ chi phối ngành công nghiệp trong một số năm tới. Nhiều hệ vật liệu thay thế đã và đang được khám phá, bao gồm các `resist` vô cơ (`Ag` pha `Se-Ge`) `[5.40]`, các `organosilane` tạo thành `SiO₂` khi được phơi `[5.41]` và các `polysilne` `[5.42]`. Các `resist` `e-beam` tiêu chuẩn như `PMMA` cũng sẵn có, dĩ nhiên. Mặc dù hiện tại chưa rõ cách tiếp cận nào trong số này cuối cùng sẽ thành công, nhưng dường như khả năng là một giải pháp sẽ được tìm ra và các `resist` với độ nhạy, độ phân giải, mật độ khuyết tật và độ bền quy trình phù hợp sẽ được phát triển cho các thế hệ công nghệ vượt quá `0,1 µm`.

Trước khi kết thúc phần này, có một số chủ đề khác mà chúng ta sẽ xem xét ngắn gọn. Bao gồm phẳng hóa (`planarization`) và các `resist` đa lớp. Những cải tiến này đối với quá trình quang khắc cơ bản nhằm cải thiện độ phân giải của ảnh được tạo ra trong `resist` hoặc cải thiện độ nhạy của `resist`. Một số kỹ thuật này hiện đang bắt đầu được sử dụng trong sản xuất.

Nhu cầu phẳng hóa trong xử lý `resist` đã được thảo luận ngắn gọn trước đó trong mối liên hệ với **Hình 5.22**. Vấn đề là địa hình bề mặt dưới `resist` sẽ gây ra sự biến thiên chiều dày trong `resist` được phủ quay. Kết quả của điều này sẽ là sự thay đổi trong quá trình phơi ở các vùng mỏng so với vùng dày. Các vùng `resist` dày sẽ bị phơi thiếu, hoặc các vùng mỏng sẽ bị phơi thừa và do đó sẽ có sự biến thiên chiều rộng vạch trong `latent image` được tạo ra trong `resist`. Từ quan điểm thực tế, các vấn đề này trở nên quan trọng nhất ở các bậc trong địa hình bên dưới vì đó là nơi có sự thay đổi đột ngột về chiều dày `resist`. Nói chung những gì quan sát được là sự thu hẹp của ảnh `resist` ngay tại bậc và sự mở rộng ảnh ngay ngoài bậc. Các hiệu ứng này trở nên rất quan trọng khi chiều cao của bậc vào cỡ kích thước đặc trưng đang được in, một tiêu chí ngày càng được đáp ứng trong công nghệ silicon khi chiều rộng vạch thu nhỏ.

Một giải pháp cho vấn đề này là phẳng hóa bề mặt wafer trước khi `resist` được phủ. Trong xử lý `backend`, ngày nay phổ biến là sử dụng đánh bóng cơ học hóa học (`CMP`) để làm điều này, như được thảo luận trong Chương `11`. `CMP` cũng đang bắt đầu được áp dụng trong xử lý `frontend`. (Xem **Hình 2.9** trong `process flow` `CMOS` ở Chương `2`.) Các lựa chọn thay thế bao gồm việc sử dụng các `resist` đa lớp, mà chúng ta sẽ thảo luận dưới đây.

**Hình 5.57** minh họa ý tưởng cơ bản đằng sau các `resist` đa lớp. Một cấu trúc hai hoặc ba lớp được sử dụng, mục đích của nó là trước tiên phẳng hóa địa hình bên dưới và sau đó tạo thành một lớp `photoresist` tương đối mỏng ở trên, đây là lớp tạo ảnh (`imaging layer`). Lớp trung gian có thể cần thiết như một lớp dừng khắc (`etch stop`) trong một số trường hợp cụ thể. Mặc dù có một số biến thể của cấu trúc này, ý tưởng cơ bản là như sau. Đầu tiên, một lớp tương đối dày được phủ quay lên wafer để phẳng hóa bề mặt. Thường thì đây chỉ đơn giản là một lớp `photoresist` không nhạy với bước sóng ánh sáng cụ thể đang được sử dụng trong hệ thống phơi chiếu. Ví dụ, `PMMA` là một `resist` `e-beam` không nhạy trong `UV` gần, có thể được sử dụng trong mối liên hệ với hệ thống phơi chiếu vạch `g` hoặc vạch `i`. Trong các hệ thống `resist` đa lớp đơn giản nhất, lớp này sau đó sẽ được nung và một lớp thứ hai mỏng hơn của `resist` được phủ quay trực tiếp lên trên. Lớp `resist` trên này nhạy với bước sóng phơi và sau khi `prebake` thích hợp, lớp `resist` này sẽ được phơi. Vì lớp `resist` tạo ảnh mỏng và đồng đều về chiều dày, một `latent image` độ phân giải cao có thể được tạo ra. Lớp tạo ảnh trên sau đó được hiện hình.
**Hình 5.57:** Cấu trúc `resist` đa lớp được thiết kế để tạo ra một lớp tạo ảnh mỏng, đồng đều phù hợp cho tạo ảnh độ phân giải cao.

---

Sử dụng lớp này bây giờ như một `mask`, lớp phẳng hóa phía dưới được phơi diện rộng bằng một nguồn `DUV`. Ở đây, điều quan trọng là lớp tạo ảnh trên không trong suốt với `DUV`, để lớp phẳng hóa phía dưới chỉ được phơi ở các vùng mà lớp trên đã được hiện hình. Với lớp `PMMA` phía dưới, việc phơi `DUV` sẽ hoạt động vì `resist` này nhạy với các bước sóng `DUV`. Về bản chất, lớp tạo ảnh mỏng đang được sử dụng như một `mask` tiếp xúc (`contact mask`) cho việc phơi lớp phía dưới. Như chúng ta đã thấy trước đó, in tiếp xúc có thể tạo ra các ảnh độ phân giải cao vì nó giảm thiểu các hiệu ứng nhiễu xạ. `Latent image` của `resist` phía dưới bây giờ được hiện hình, tạo ra một lớp `resist` có mẫu sau đó có thể được sử dụng để khắc các lớp bên dưới hoặc làm `mask` cấy ion.

Một lựa chọn thay thế cho quy trình trên sử dụng lớp dừng khắc trung gian cũng được trình bày trong **Hình 5.57**. Ở đây, lớp bổ sung này được lắng đọng giữa lớp phẳng hóa và lớp tạo ảnh. Thường thì đây có thể là một lớp `SiO₂` được lắng đọng từ nguồn thủy tinh phủ quay (`spun on glass`), hoặc nó có thể được lắng đọng bằng `PECVD` ở nhiệt độ thấp có thể chịu được bởi lớp phẳng hóa. Quá trình phơi và hiện hình của lớp tạo ảnh trên tiến hành như đã mô tả trước đó. Tuy nhiên, việc khắc bây giờ được sử dụng để chuyển mẫu vào lớp phẳng hóa phía dưới. Đầu tiên, khắc ion phản ứng (`RIE`) được dùng để khắc lớp dừng khắc trung gian sử dụng `resist` tạo ảnh làm `mask`. Vì lớp `resist` tạo ảnh mỏng, nhiều khả năng sẽ không thể sử dụng lớp này làm `mask` trong quá trình khắc `RIE` xuyên suốt toàn bộ lớp phẳng hóa dày bên dưới. Do đó, lớp dừng khắc được sử dụng như một lớp chuyển mẫu trung gian. Một khi mẫu được khắc vào lớp dừng khắc, việc khắc `RIE` của lớp phẳng hóa phía dưới sau đó chuyển mẫu vào lớp đó. Nếu `PMMA` hoặc một vật liệu hữu cơ khác được sử dụng cho lớp phía dưới, có thể sử dụng quy trình `RIE` bằng `O₂` để khắc lớp này. Quy trình này có độ chọn lọc cao đối với lớp trung gian (`SiO₂` ví dụ) và do đó có thể sử dụng lớp dừng khắc tương đối mỏng. Dù sử dụng `process flow` hai lớp hay ba lớp, các ý tưởng then chốt là phẳng hóa địa hình bên dưới, sau đó là phơi một lớp `resist` tạo ảnh mỏng có độ phân giải cao.

Các `resist` đa lớp chưa tìm thấy ứng dụng rộng rãi trong sản xuất tại thời điểm này, chủ yếu vì quy trình phức tạp hơn không khả thi về mặt kinh tế do mật độ khuyết tật cao. Tuy nhiên, khi các kích thước đặc trưng tối thiểu tiếp tục thu nhỏ, khái niệm về một lớp tạo ảnh mỏng và đồng đều ngày càng trở nên hấp dẫn và cách tiếp cận này có thể được sử dụng trong tương lai `[5.43]`.

Một biến thể khác trong các cấu trúc `resist` đa lớp này là làm cho lớp phẳng hóa phía dưới đóng vai trò lớp phủ chống phản xạ (`ARC`) cũng như lớp phẳng hóa. Trong trường hợp này, vật liệu được chọn cho lớp phẳng hóa có độ hấp thụ cao tại bước sóng phơi và không tẩy trắng đáng kể. Do đó, các photon đi qua lớp `resist` tạo ảnh mỏng phía trên sẽ bị hấp thụ bởi lớp phẳng hóa và sẽ không phản xạ từ các đặc trưng đế bên dưới. Vì vậy, thuật ngữ lớp phủ chống phản xạ được áp dụng cho các lớp như vậy. Một khi `latent image` được hình thành trong lớp tạo ảnh trên, nó có thể được chuyển qua lớp phẳng hóa (`ARC`) phía dưới bằng khắc khô sau khi hiện hình. Các lớp `ARC` hữu ích trong các `resist` `DNQ` để giảm thiểu các hiệu ứng sóng dừng (**Hình 5.24**). Chúng thiết yếu trong các `resist` `DUV` vì các `resist` này không tẩy trắng và do đó các phản xạ là một vấn đề lớn hơn xuyên suốt quá trình phơi.

---

## 5.7 Tóm tắt các ý chính

Quang khắc là một trong những công nghệ nền tảng mà các `IC` hiện đại dựa trên đó. Hai yếu tố then chốt của các hệ thống quang khắc quang học hiện đại là thiết bị phơi chiếu và `photoresist`. Các thiết bị phơi chiếu ngày nay nói chung sử dụng quang học chiếu ảnh với các thấu kính khúc xạ bị giới hạn bởi nhiễu xạ. Các hệ thống này có thể in một vùng vào cỡ vài `cm²` trên wafer để phải sử dụng cách tiếp cận `step and repeat` hoặc `step and scan` để in toàn bộ wafer. Các `resist` vạch `g` và vạch `i` ngày nay chủ yếu dựa trên các vật liệu `DNQ`, được sử dụng cho sản xuất xuống đến thế hệ `0,35 µm`. Các `resist` `DUV` sử dụng khuếch đại hóa học được dùng trong thế hệ công nghệ `0,25 µm` và phù hợp cho một số thế hệ tương lai. Các công cụ mô phỏng quang khắc dựa trên hai lĩnh vực khoa học, quang học Fourier để mô tả hiệu năng của các thiết bị phơi chiếu và hóa học `resist` để mô tả sự hình thành mẫu `mask` trong `resist`. Các công cụ này ngày nay rất hữu ích trong việc hiểu và tối ưu hóa hiệu năng của các hệ thống quang khắc.

Một thay đổi lớn trong cách thức in các mẫu lên wafer nhiều khả năng sẽ phải xảy ra trong vòng `10` năm tới. Dường như không thể mở rộng các kỹ thuật quang khắc quang học ngày nay vượt quá nhiều so với thế hệ `0,1 µm`. Các lựa chọn tồn tại để thay thế quang khắc quang học, nhưng không có lựa chọn nào rõ ràng là khả thi ngày nay. Tuy nhiên, nếu lịch sử là bài học, các giải pháp sẽ được tìm ra cho vấn đề quang khắc, cho phép tiếp tục thu nhỏ trong các kích thước đặc trưng bán dẫn.

---

## 5.8 Tài liệu tham khảo

[5.1]. "National Technology Roadmap for Semiconductors," SIA, 1997.

[5.2]. J. W. Goodman, Introduction to Fourier Optics, McGraw Hill, New York, 1968.

[5.3]. C. A. Mack, Inside Prolith, a Comprehensive Guide to Optical Lithography Simulation, Finle Technologies, Austin TX, 1997.

[5.4]. W. M. Moreau, Semiconductor Lithography Principles, Practices and Materials, Plenum Press, New York, 1988.

[5.5]. W. Waldo, "Techniques and Tools for Optical Lithography" in Handbook of VLSI Microlithography Principles, Technology and Applications, edited by W. B. Glendinning and J. N. Helbert, Noyes Publications, NJ, 1991.

[5.6]. B. J. Lin, "Electromagnetic Near-Field Diffraction Pattern of a Medium Slit," J. Opt. Soc. of Amer., vol. 62, p. 976, 1972.

[5.7]. H. Ito, C. G. Willson, "Polymers in Electronics," T. Davidson, ed., Symposium Series 242, American Chemical Society, Washington D. D. p. 11, 1984.

[5.8]. D. Seeger, "Chemically Amplified Resists for Advanced Lithography: Road to Success or Detour?" Solid State Tech., p. 115, June 1997.

[5.9]. D. Wallraff et. al. "Single Layer Chemically Amplified Photoresists for 193 nm Lithography," J. Vac. Sci. Tech., vol. B11, p. 2783, 1993.

[5.10]. H. Ito, "Deep-UV Resists: Evolution and Status," Solid State Tech., p. 164, July 1996.

[5.11]. H. Ito, "Chemical Amplification Resists: History and Development Within IBM," IBM J. Res. and Dev., vol. 41, p. 69, 1997.

[5.12]. M. D. Levenson, "Extending the Lifetime of Optical Lithography Technologies with Wavefront Engineering," Jpn. J. Appl. Phys., vol. 33, p. 6765, 1994.

[5.13]. J. P. Stirniman and M. L. Rieger, Proc. SPIE, vol. 2197, 294, 1994.

[5.14]. M. D. Levenson, N. S. Visnwathen and R. A. Simpson, "Improving Resolution in Photolithography with a Phase Shifting Mask," IEEE Trans. Elec. Dev., vol. ED-29, p. 1828, 1982.

[5.15]. R. Larrabee, L. Linholm and M. T. Postek, "Microlithography Metrology" in Handbook of VLSI Microlithography Principles, Technology and Applications, edited by W. B. Glendinning and J. N. Helbert, Noyes Publications, NJ, 1991.

[5.16]. D. Nyyssonen and R. D. Larrabee, "Submicrometer Linewidth Metrology in the Optical Microscope," J. Res. Natl. Bur. Stand., vol. 92, p. 187, 1987.

[5.17]. M. G. Buehler, "Microelectronic Test Chips for VLSI Electronics," in VLSI Electronics: Microstructure Science, vol. 6, p. 529, Academic Press, Inc., 1983.

[5.18]. T. F. Hasan and D. S. Perloff, "Automated Electrical Measurement Techniques to Control VLSI Linewidth, Resistivity and Registration," Test and Measurement World, vol. 5, p. 78, 1985.

[5.19]. D. K. Schroder, Semiconductor Material and Device Characterization, John Wiley and Sons, New York, 1990.

[5.20]. F. H. Dill, "Optical Lithography," IEEE Trans. Elec. Dev., vol. ED-22, p. 440, 1975.

[5.21]. F. H. Dill, W. P. Hornberger, P. S. Hauge and J. M. Shaw, "Characterization of Positive Photoresist," IEEE Trans. Elec. Dev., vol. ED-22, p. 445, 1975.

[5.22]. K. L. Konnerth and F. H. Dill, "In-Situ Measurement of Dielectric Thickness During Etching of Developing Processes," IEEE Trans. Elec. Dev., vol. ED-22, p. 452, 1975.

[5.23]. F. H. Dill, A. R. Neureuther, J. A. Tuttle and E. J. Walker, "Modeling Projection Printing of Positive Photoresists," IEEE Trans. Elec. Dev., vol. ED-22, p. 456, 1975.

[5.24]. W. G. Oldham, S. N. Nandgaonkar, A. R. Neureuther and M. O'Toole, "A General Simulator for VLSI Lithography and Etching Processes: Part 1 - Application to Projection Lithography," IEEE Trans. Elec. Dev., vol. ED-26, p. 717, 1979.

[5.25]. C. A. Mack, "PROLITH: a Comprehensive Optical Lithography Model," Optical Microlithography IV, Proc. SPIE, vol. 538, p. 207, 1985.

[5.26]. DEPICT User's manual, Dec. 1996, Avant! Inc.

[5.27]. ATHENA User's Manual, Oct. 1996, Silvaco Inc.

[5.28]. C. A. Mack, "Analytical Expression for the Standing Wave Intensity in Photoresist," Appl. Optics, vol. 25, p. 1958, 1986.

[5.29]. C. A. Mack, "Absorption and Exposure in Positive Photoresists," Appl. Optics, vol. 27, p. 4913, 1988.

[5.30]. F. H. Dill and J. M. Shaw, "Thermal Effects on the Photoresist AZ1350J," IBM Journal Res. and Dev., vol. 21, p. 210, 1977.

[5.31]. C. A. Mack and R. T. Carback, "Modeling the Effects of Prebake on Positive Resist Processing," Proc. of Kodak Microelectronics Seminar, p. 155, 1985.

[5.32]. E. J. Walker, "Reduction of Photoresist Standing-Wave Effects by Post-Exposure Bake," IEEE Trans. Elec. Dev., vol. ED-22, p. 464, 1975.

[5.33]. C. A. Mack, "New Kinetic Model for Resist Dissolution," J. Electrochem. Soc., vol. 139, p. L35, 1992.

[5.34]. A. N. Broers, W. W. Molzen, J. J. Cuomo and N. D. Wittels, "Electron Beam Fabrication of 80 Å Metal Structures," Appl. Phys. Lett., vol. 29, 1976.

[5.35]. C. Y. Chang, G. Owen, R. F. Pease and T. Kailath, "A Computational Method for the Correction of Proximity Effects in Electron-Beam Lithography," Electron-Beam, X-ray and Ion Beam Submicron Lithographies, Proc. SPIE, vol. 1671, p. 208, 1992.

[5.36]. S. D. Berger and J. M. Gibson, "New Approach to Projection-Electron Lithography with Demonstrated 0.1 µm Linewidth," Appl. Phys. Lett., vol. 57, p. 153, 1990.

[5.37]. L. R. Harriott, "Preliminary Results From a Prototype Projection Electron-Beam Stepper - SCALPEL Proof-of-Concept System," J. Vac. Sci. Tech., vol. B14, p. 3825, 1996.

[5.38]. E. Spiller, "Reflective Multilayer Coatings for the Far UV Region," Appl. Optics, vol. 15, p. 2333, 1975.

[5.39]. A. M. Hawryluk, N. M. Ceglio and D. A. Markle, "EUV Lithography," Solid State Tech., p. 151, 1997.

[5.40]. Y. Yoshikawa, O. Ochi, H. Nagai and Y. Mizushima, "A Novel Inorganic Photoresist Utilizing Ag Photodoping in Se-Ge Glass Films," Appl. Phys. Lett., vol. 29, p. 677, 1977.

[5.41]. D. C. Hofer, R. D. Miller and C. G. Willson, "Polysilane Bilayer UV Lithography," SPIE Proc., vol. 469, p. 16, 1984.

[5.42]. R. R. Kunz, P. A. Bianconi, M. W. Horn, R. R. Paladuga, D. C. Shaver, D. A. Smith and C. A. Freed, "Polsilyne Resists for 193 nm Excimer Laser Lithography," Advances in Resist Technology and Processing VIII, SPIE Proc., vol. 1446, p. 218, 1991.

[5.43]. D. E. Seeger, D. C. La Turlipe Jr., R. R. Kunz, C. M. Garza and M. A. Hanratty, "Thin-Film Imaging: Past, Present, Prognosis," IBM J. Res. and Dev., vol. 41, p. 105, 1997.

---

## 5.9 Bài tập

**5.1.** Tính toán và vẽ đồ thị theo bước sóng phơi độ phân giải lý thuyết và độ sâu tiêu cự đối với một hệ thống phơi chiếu chiếu ảnh có `NA = 0,6` (xấp xỉ tốt nhất có thể đạt được ngày nay). Giả sử `k₁ = 0,6` và `k₂ = 0,5` (cả hai đều là các giá trị điển hình). Xem xét các bước sóng giữa `100 nm` và `1000 nm` (ánh sáng `DUV` và khả kiến). Chỉ ra các bước sóng phơi phổ biến đang được sử dụng hoặc đang được xem xét ngày nay trên đồ thị của bạn (vạch `g`, vạch `i`, `KrF` và `ArF`). Nguồn `ArF` có đủ cho các thế hệ công nghệ `0,13 µm` và `0,1 µm` theo các tính toán đơn giản này không?

**5.2.** Trong một quy trình `resist` dương cụ thể, đôi khi nhận thấy rằng có khó khăn trong việc hiện hình hết vài trăm angstrom cuối cùng của `resist` ở các vùng đã phơi. Điều này đôi khi gây ra các vấn đề khắc vì `resist` vẫn còn ở các vùng cần được khắc. Đề xuất một nguyên nhân có thể của vấn đề này và do đó đề xuất một giải pháp.

**5.3.** Một hệ thống phơi chiếu tia X sử dụng các photon có năng lượng `1 keV`. Nếu khoảng cách giữa `mask` và wafer là `20 µm`, ước lượng độ phân giải bị giới hạn bởi nhiễu xạ có thể đạt được bởi hệ thống này.

**5.4.** Ước lượng bước sóng phơi được sử dụng trong ví dụ mô phỏng trong **Hình 5.44** trong văn bản. Giả sử chiết suất của `photoresist` là `1,68` (giá trị điển hình).

**5.5.** Trong chương này, chúng ta đã xem xét một ví dụ về một khe cô lập trên `mask` và thấy rằng phép biến đổi Fourier của mẫu này là hàm `sin(x)/x`. Hàm này mô tả sự biến thiên không gian của cường độ ánh sáng mà thấu kính vật kính phải thu nhận. Một ví dụ minh họa hơn về các hiệu ứng nhiễu xạ được cho bởi một mẫu `mask` bao gồm mẫu tuần hoàn của các vạch và khe như trình bày dưới đây.

Tìm phép biến đổi Fourier cho hàm `mask` này và vẽ đồ thị như đã làm trong ví dụ trong chương. Thấu kính vật kính phải thu nhận ít nhất bậc nhiễu xạ thứ nhất nếu nó sẽ phân giải các đặc trưng với bước `p`. Sử dụng tiêu chí này để suy ra một phương trình giống như Phương trình `5.2` cho độ phân giải của hệ thống như vậy.

**5.6.** Giả sử rằng **Hình 5.46** trong văn bản được xác định thực nghiệm cho một `resist` dày `0,6 µm` với chiết suất `1,68`. Ước lượng các tham số `resist` Dill từ dữ liệu trong hình này.

**5.7.** Quang khắc thường phải được thực hiện trên địa hình bên dưới trên một chip silicon. Điều này có thể dẫn đến sự biến thiên chiều dày `resist` khi địa hình bên dưới lên xuống. Điều này đôi khi có thể gây ra một số phần của ảnh `photoresist` bị phơi thiếu và/hoặc các vùng khác bị phơi thừa. Giải thích theo hóa học của quá trình phơi `resist` tại sao các vấn đề phơi thiếu và phơi thừa này xảy ra.

**5.8.** Như được mô tả trong chương này, không có lựa chọn rõ ràng nào cho các hệ thống quang khắc vượt qua các công cụ chiếu ảnh quang học dựa trên laser excimer `ArF` `193 nm`. Một khả năng là một hệ thống chiếu ảnh quang học sử dụng laser excimer `F₂` `157 nm`. a). Giả sử khẩu độ số là `0,8` và `k₁ = 0,75`, độ phân giải dự kiến của hệ thống như vậy là gì theo ước lượng bậc nhất về độ phân giải? b). Các dự báo thực tế cho các hệ thống như vậy gợi ý rằng chúng có thể có khả năng phân giải các đặc trưng phù hợp cho thế hệ `0,07 µm` năm `2009`. Đề xuất ba cách tiếp cận để thực sự đạt được độ phân giải này với các hệ thống này.

**5.9.** Các công cụ quang khắc chiếu ảnh quang học hiện tại tạo ra các `aerial image` bị giới hạn bởi nhiễu xạ. Một `aerial image` điển hình được tạo ra bởi hệ thống như vậy được trình bày trong mô phỏng dưới đây, trong đó các vùng `mask` hình vuông và hình chữ nhật tạo ra ảnh được trình bày. (Các đặc trưng `mask` là các đường viền đen, `aerial image` được tính toán là thang xám bên trong các hình chữ nhật đen.) Đặc điểm chính của `aerial image` là các góc bo tròn so với các góc vuông sắc nét của mẫu mong muốn. Giải thích về mặt vật lý tại sao các đặc trưng này trông như chúng trông, sử dụng lý thuyết nhiễu xạ và các tính chất vật lý của các công cụ quang khắc chiếu ảnh quang học hiện đại.

**5.10.** Các hệ thống quang khắc quang học tương lai nhiều khả năng sẽ sử dụng các bước sóng phơi ngắn hơn để đạt được độ phân giải cao hơn và chúng cũng nhiều khả năng sẽ sử dụng các kỹ thuật phẳng hóa để cung cấp các đế "phẳng" để phơi các lớp `resist`. Giải thích tại sao.
# CHƯƠNG 6: OXY HÓA NHIỆT VÀ MẶT TIẾP XÚC Si/SiO₂

## 6.1 Giới thiệu

Silicon là vật liệu độc đáo trong số các vật liệu bán dẫn ở chỗ bề mặt của nó có thể được thụ động hóa dễ dàng bằng một lớp oxide. Mặt tiếp xúc giữa `Si` và `SiO₂` có lẽ là mặt tiếp xúc vật liệu được nghiên cứu kỹ lưỡng nhất trong số tất cả các mặt tiếp xúc vật liệu, và các tính chất điện lẫn cơ học của nó cũng như của bản thân lớp oxide gần như là lý tưởng. Các lớp `SiO₂` có thể dễ dàng được mọc nhiệt trên silicon hoặc lắng đọng lên nhiều đế khác nhau. Chúng bám dính tốt, chúng chặn sự khuếch tán của các chất pha tạp và nhiều tạp chất không mong muốn khác, chúng bền với hầu hết các hóa chất được sử dụng trong xử lý silicon và thế mà vẫn có thể dễ dàng tạo mẫu và khắc bằng các hóa chất cụ thể hoặc khắc khô bằng plasma, chúng là các chất cách điện tuyệt vời và có các tính chất khối ổn định và có thể tái tạo. Mặt tiếp xúc hình thành giữa `Si` và `SiO₂` có rất ít khuyết tật cơ học hay điện và ổn định theo thời gian. Các tính chất này làm cho các cấu trúc `MOS` dễ xây dựng trong silicon và hàm ý rằng các linh kiện silicon thuộc mọi loại nói chung đáng tin cậy và ổn định. Hầu như tất cả các tổ hợp bán dẫn/chất cách điện khác đều gặp phải một hoặc nhiều vấn đề làm hạn chế đáng kể khả năng ứng dụng của chúng.

Chúng ta đã thấy một số ứng dụng của các lớp `SiO₂` trong ví dụ công nghệ `CMOS` ở Chương `2`. Bao gồm việc sử dụng làm lớp điện môi cổng trong các linh kiện `MOS`, làm `mask` chống cấy ion, làm vùng cách điện theo chiều ngang giữa các linh kiện lân cận và làm chất cách điện giữa các lớp kim loại trong xử lý `backend`. Các ứng dụng này và một số ứng dụng khác được minh họa trong **Hình 6.1**.

---

**Hình 6.1:** Các ứng dụng của `SiO₂` trong công nghệ silicon.

---

`SIA NTRS` cung cấp lộ trình cho `SiO₂` và các lớp cách điện khác như một phần trong các yêu cầu công nghệ chung của nó. Một số vấn đề then chốt được tóm tắt trong **Bảng 6.1** `[6.1]`. Hầu hết các yêu cầu này liên quan đến các oxide `< 10 nm` vì đây là các chất cách điện cổng và oxide đường hầm (`tunneling oxide`) quan trọng trong các cấu trúc `MOS` hiện đại. Hai hàng cuối trong bảng liên quan đến các chất cách điện dày hơn được sử dụng chủ yếu để che chắn và trong xử lý `backend`. Các lớp cách điện này thường được lắng đọng thay vì mọc nhiệt và sẽ được thảo luận chi tiết hơn trong Chương `9` và `11`.

---

> **[Bảng thông số]**

| Hạng mục | 1997 | 1999 | 2003 | 2006 | 2009 | 2012 |
|---|:---:|:---:|:---:|:---:|:---:|:---:|
| Năm giao lô `DRAM` đầu tiên | 1997 | 1999 | 2003 | 2006 | 2009 | 2012 |
| Kích thước đặc trưng tối thiểu | 0,25µ | 0,18µ | 0,13µ | 0,10µ | 0,07µ | 0,05µ |
| Số bit/Chip `DRAM` | 256M | 1G | 4G | 16G | 64G | 256G |
| Điện áp cấp tối thiểu (V) | 1,8–2,5 | 1,5–1,8 | 1,2–1,5 | 0,9–1,2 | 0,6–0,9 | 0,5–0,6 |
| Oxide cổng `Tox` tương đương (nm) | 4–5 | 3–4 | 2–3 | 1,5–2 | <1,5 | <1,0 |
| Kiểm soát chiều dày (`% 3σ`) | ±4 | ±4 | ±4–6 | ±4–8 | ±4–8 | ±4–8 |
| Điện trường tối đa tương đương (MV cm⁻¹) | 4–5 | 5 | 5 | >5 | >5 | >5 |
| Dòng rò oxide cổng (`DRAM`) (pA µm⁻²) | <0,01 | <0,01 | <0,01 | <0,01 | <0,01 | <0,01 |
| Oxide đường hầm (nm) | 8,5 | 8 | 7,5 | 7 | 6,5 | 6 |
| Số mức dây tối đa | 6 | 6–7 | 7 | 7–8 | 8–9 | 9 |
| Hằng số điện môi `κ`, cho chất cách điện giữa các kim loại | 3,0–4,1 | 2,5–3,0 | 1,5–2,0 | 1,5–2,0 | <1,5 | <1,5 |

**Bảng 6.1:** Các dự báo tương lai cho công nghệ silicon lấy từ `SIA NTRS` `[6.1]`.

---

Ngay ở nhiệt độ phòng, silicon tiếp xúc với môi trường oxy hoặc không khí sẽ hình thành một lớp oxide bản địa (`native oxide`) mỏng trên bề mặt của nó. "Oxide" này nói chung không phải là `SiO₂` đúng hóa học và thường chứa hỗn hợp `SiO` + carbon + các chất nhiễm bẩn khác tùy thuộc vào môi trường wafer. Oxide này nhanh chóng phủ bề mặt đến chiều dày `0,5 - 1 nm` (`5 - 10 Å`). Tốc độ mọc sau đó chậm lại và thực sự dừng lại sau vài giờ, với chiều dày cuối cùng vào cỡ `1 - 2 nm`. Cả tốc độ mọc lẫn chiều dày oxide bản địa cuối cùng đều phụ thuộc vào quá trình chuẩn bị bề mặt và đặc biệt vào sự có hay không có của các cặn hóa học từ các quy trình làm sạch. Ví dụ, các quy trình làm sạch `SC-1` và `SC-2` mà chúng ta đã thảo luận trong Chương `4` tạo ra các oxide hóa học trên bề mặt silicon thường dày `1 - 2 nm`.

Ứng dụng quan trọng nhất của các chất cách điện trong công nghệ `CMOS` là làm chất cách điện cổng. Như trình bày trong **Bảng 6.1**, các lớp này thường dày `3 - 5 nm` trong công nghệ tiên tiến nhất hiện tại và được dự báo sẽ `< 1 nm` trong `10 - 15` năm tới. Ngay cả ngày nay, các lớp này chỉ dày khoảng `25 - 50` lớp nguyên tử. Thật đáng chú ý là các chip `VLSI` có thể được chế tạo ngày nay với hàng chục triệu oxide như vậy, mỗi cái không có khuyết tật và có khả năng chịu đựng một cách đáng tin cậy các điện trường trong khoảng cỡ hệ số hai của giới hạn vật liệu của `SiO₂` là khoảng `10 - 15 MV cm⁻¹`. Cũng lưu ý trong **Bảng 6.1** rằng các chất cách điện cổng phải được kiểm soát chiều dày về cơ bản đến từng khoảng cách nguyên tử đơn. Sự thu nhỏ tiếp tục sẽ làm cho các màng `SiO₂` rất khó đáp ứng tất cả các yêu cầu này. Kết quả là, rất có thể các chất cách điện cổng rất mỏng được dự báo cho tương lai sẽ không phải là các màng `SiO₂` thuần túy. Các màng oxynitride (`SiO₂` với nitơ được đưa vào thông qua nhiều quá trình khác nhau) là giải pháp gần hạn có khả năng nhất.

Với các màng mỏng như được dự báo trong `NTRS`, thuật ngữ "chất cách điện" bắt đầu mất đi một phần ý nghĩa của nó vì các màng mỏng như vậy sẽ dẫn một lượng hữu hạn dòng điện do sự đường hầm cơ học lượng tử (`quantum mechanical tunneling`) của các electron hoặc lỗ trống. Quá trình này xảy ra do bản chất sóng của electron và về cơ bản cho phép các electron đi qua một rào cản không thể xuyên qua như `SiO₂`, nếu rào cản đủ mỏng. Xác suất của sự kiện như vậy xảy ra giảm theo hàm mũ với chiều dày oxide, vì vậy các oxide đường hầm phải khá mỏng để dòng điện đáng kể chảy qua. Nếu một cổng polysilicon được lắng đọng lên trên một oxide như vậy và được cách điện bằng cách bao quanh nó bằng `SiO₂` ở tất cả các mặt, thì các electron đường hầm qua oxide mỏng bên dưới polysilicon có thể bị bẫy trong lớp poly, cho phép nó nhận điện tích âm. Điều này có thể được sử dụng làm cơ sở cho một phần tử bộ nhớ không bay hơi (`non-volatile memory`). Trên thực tế, các lớp oxide từ `4` đến `10 nm` thường được sử dụng trong các bộ nhớ có thể lập trình điện và được gọi là các oxide đường hầm trong các ứng dụng này.

Trong các điện môi cổng, sự đường hầm là không mong muốn và trong một số ứng dụng như các transistor đọc `DRAM` là một vấn đề lớn vì nó trực tiếp ảnh hưởng đến việc lưu trữ dữ liệu. Các thông số kỹ thuật về dòng rò được trình bày trong **Bảng 6.1** đối với `DRAM` nhiều khả năng không thể đạt được trong các lớp `SiO₂` mỏng hơn khoảng `4 nm`, và do đó có khả năng các điện môi cổng dày hơn sẽ được sử dụng trong các ứng dụng này. Đối với các ứng dụng logic mục đích chung hơn, mức độ dòng rò cổng cao hơn có thể chấp nhận được.

Nhiều ứng dụng khác được liệt kê trong **Hình 6.1** đã được thảo luận chi tiết trong Chương `2`. Các oxide nhiệt trong khoảng `10 - 30 nm` thường được sử dụng dưới các lớp `Si₃N₄` như các oxide giảm ứng suất (`stress relief`) hay oxide "đệm" (`pad oxide`) trong các quy trình kiểu `LOCOS`. Chúng ta đã thấy một số ví dụ về ứng dụng này trong `process flow` `CMOS` ở Chương `2`. Các oxide nhiệt dày hơn thường phục vụ làm `mask` cho các bước cấy ion hoặc pha tạp pha khí. Ở đây, thường chỉ quan trọng là lớp oxide đủ dày để chặn sự thâm nhập của chất pha tạp vào đế silicon bên dưới. Chúng ta sẽ xem xét các ứng dụng này cẩn thận hơn trong Chương `7` và `8`. Các oxide dày cũng có thể phục vụ làm oxide "trường" (`field oxide`) hay oxide cách điện trong nhiều công nghệ. Trong trường hợp này, chúng cung cấp sự cách điện theo chiều ngang giữa các linh kiện lân cận trên bề mặt wafer.

Cũng hoàn toàn có thể lắng đọng các lớp `SiO₂` bằng các kỹ thuật `CVD` hoặc `LPCVD`. Đối với các ứng dụng `backend`, sau khi các wafer có kim loại trên chúng, lắng đọng là lựa chọn duy nhất. Trên thực tế, đối với bất kỳ ứng dụng nào mà oxide phải được đặt lên trên các màng bên dưới, lắng đọng thường là lựa chọn duy nhất vì silicon có thể không có sẵn từ các màng bên dưới để mọc `SiO₂` nhiệt. Lắng đọng thường liên quan đến "ngân sách nhiệt" (`thermal budget`) nhỏ hơn nhiều so với oxy hóa nhiệt và do đó được ưu tiên ngay cả trong các quy trình `frontend` khi điều quan trọng là giới hạn chu trình nhiệt độ mà các wafer phải chịu. Các oxide lắng đọng thường không được sử dụng cho các lớp mỏng hơn khoảng `10 nm` vì việc kiểm soát quá trình lắng đọng không tốt như quá trình oxy hóa nhiệt. Mặt tiếp xúc giữa một oxide lắng đọng và silicon bên dưới cũng không hoàn hảo về mặt điện như mặt tiếp xúc được hình thành bởi một oxide nhiệt, vì vậy các oxide nhiệt thường được sử dụng cho các điện môi cổng và các oxide quan trọng khác trong các cấu trúc linh kiện. Tuy nhiên, có thể ủ một mặt tiếp xúc oxide lắng đọng/`Si` để tạo ra các tính chất điện gần với những tính chất của một oxide được mọc nhiệt. Cách đơn giản nhất để "ủ" một mặt tiếp xúc như vậy là đơn giản mọc một oxide nhiệt mỏng bên dưới oxide lắng đọng. Điều này đơn giản để thực hiện vì `SiO₂` mới luôn mọc tại mặt tiếp xúc `Si/SiO₂`, như chúng ta sẽ thấy trong phần tiếp theo.

Cuối cùng, lưu ý rằng `NTRS` trong **Bảng 6.1** quy định hằng số điện môi nhỏ hơn `3,9` (`SiO₂`) cho các chất cách điện giữa các kim loại trong các thế hệ công nghệ trong tương lai. Điều này cần thiết để cải thiện tốc độ của các dây nối (`interconnects`) (độ trễ `RC`) và hàm ý rằng các màng lắng đọng sẽ không phải là `SiO₂` trong các quy trình `backend` trong tương lai. Chúng ta sẽ thảo luận về các chất điện môi lắng đọng có hằng số điện môi thấp ("low `κ`") trong Chương `11`. Trái ngược với các chất điện môi "low `κ`" trong `backend`, các oxide cổng nhiều khả năng sẽ sử dụng các chất điện môi "high `κ`" trong tương lai. Do đó, các chiều dày oxide cổng điện tương đương trong **Bảng 6.1** có thể được đạt được với các vật liệu `κ` cao hơn dày hơn về mặt vật lý so với các giá trị trong bảng.

Chương này sẽ tập trung chủ yếu vào quá trình oxy hóa nhiệt và các tính chất của mặt tiếp xúc `Si/SiO₂`. Các oxide lắng đọng và các màng mỏng lắng đọng khác được mô tả chi tiết trong Chương `9`.

---

## 6.2 Sự phát triển lịch sử và các khái niệm cơ bản

Một số thí nghiệm được thực hiện trong ba mươi năm qua `[6.2 - 6.5]` đã chứng minh một cách thuyết phục rằng khi silicon bị oxy hóa, quá trình oxy hóa xảy ra tại mặt tiếp xúc `Si/SiO₂` như minh họa trong **Hình 6.2**. Vì điều này, một mặt tiếp xúc mới liên tục hình thành và di chuyển xuống phía dưới vào đế silicon. Do đó, sự oxy hóa silicon xảy ra bằng sự khuếch tán vào trong của chất oxy hóa, thay vì sự khuếch tán ra ngoài của silicon. Về mặt khái niệm, cách đơn giản nhất để chứng minh điều này là mọc một lớp `SiO₂` với một đồng vị oxy và sau đó tiếp tục mọc với một đồng vị thứ hai (ví dụ `O¹⁶` và `O¹⁸`). Việc phân tích biên dạng qua lớp oxide hợp thành thu được bằng một kỹ thuật nhạy cảm với khối lượng có thể xác định oxide thứ hai mọc ở bề mặt trên hay bề mặt dưới. Các thí nghiệm này và các thí nghiệm liên quan khác đã nhất quán chỉ ra rằng oxide mới mọc tại mặt tiếp xúc `Si/SiO₂`.

---

**Hình 6.2:** Quá trình cơ bản của sự oxy hóa silicon. Phản ứng hóa học xảy ra tại mặt tiếp xúc `Si/SiO₂`.

---

Về mặt khái niệm, người ta có thể nghĩ về quá trình này theo cách sau. Các nguyên tử `Si` trong đế được liên kết với các nguyên tử `Si` khác. Các liên kết này phải được phá vỡ, các nguyên tử oxy được chèn vào giữa các nguyên tử silicon, và cuối cùng các liên kết `Si-O` được hình thành. Quá trình liên quan đến sự giãn nở thể tích vì cần không gian cho các nguyên tử oxy. Như minh họa ở giữa **Hình 6.3**, oxide muốn giãn nở `30%` theo cả ba chiều để chứa các nguyên tử oxy. Tuy nhiên, vì đế silicon ngăn cản sự giãn nở theo hai chiều ngang, lựa chọn duy nhất là oxide giãn nở lên phía trên như trình bày ở bên phải của **Hình 6.3**. Thể tích do đó được bù bởi sự giãn nở `2,2` lần lên phía trên của oxide so với thể tích silicon bị oxy hóa.

**Hình 6.4** minh họa điều này trong một cấu trúc hai chiều thực tế. Ví dụ này là một mặt cắt ngang `SEM` của một quy trình `LOCOS` đơn giản giống như quy trình chúng ta đã mô tả trong Chương `2`. Trên các bề mặt phẳng, hầu hết sự giãn nở thể tích được bù đơn giản bằng cách oxide mọc lên trên bề mặt silicon ban đầu như trong **Hình 6.3**. Trên các bề mặt có hình dạng, phổ biến đặc biệt trong các cấu trúc linh kiện silicon tiên tiến, sự giãn nở có thể không được bù dễ dàng như vậy. `LOCOS` dẫn đến một mặt tiếp xúc `Si/SiO₂` không phẳng giữa các vùng bị che bởi nitride và vùng được oxy hóa, và một vùng chuyển tiếp rõ ràng giữa hai vùng. Vùng chuyển tiếp này có dạng đặc trưng "mỏ chim" (`bird's beak`) do sự oxy hóa theo chiều ngang bên dưới `mask` nitride. Mặc dù **Hình 6.3** đại diện cho những gì xảy ra trong cấu trúc `LOCOS` thực xa khỏi `mask` nitride, tình huống rõ ràng phức tạp hơn nhiều trong các cấu trúc có hình dạng.

---

**Hình 6.3:** Sự giãn nở thể tích xảy ra trong quá trình oxy hóa silicon. Một đơn vị thể tích silicon ở bên trái được chuyển đổi thành `SiO₂`. Ở giữa, sự giãn nở thể tích không bị ràng buộc; ở bên phải, đế hạn chế sự giãn nở theo một chiều.

---

**Hình 6.4:** Ảnh kính hiển vi điện tử quét của một cấu trúc `LOCOS` đơn giản. Sự oxy hóa silicon được che bên phải bởi một lớp `Si₃N₄`. Một lớp polysilicon đã được lắng đọng lên trên cấu trúc, sau khi lớp `Si₃N₄` được tẩy, để cung cấp độ tương phản trong ảnh. Lưu ý rằng oxide được mọc ở bên trái chiếm xấp xỉ gấp đôi thể tích của silicon được tiêu thụ trong quá trình oxy hóa. Ảnh do J. Bravman, Đại học Stanford cung cấp.

---

Các lớp oxide mọc trên silicon là vô định hình (`amorphous`). Điều này ban đầu có thể ngạc nhiên vì chúng ta đang oxy hóa một đế đơn tinh thể và `SiO₂` tồn tại ở cả dạng tinh thể lẫn vô định hình. Tuy nhiên, không có dạng tinh thể nào của `SiO₂` có kích thước mạng khớp chặt với đế silicon. Bất kỳ nỗ lực nào để mọc `SiO₂` đơn tinh thể trên silicon do đó sẽ dẫn đến các ứng suất rất lớn. Các ứng suất như vậy có thể dễ dàng đủ lớn để tạo ra các khuyết tật kết tinh học trong silicon, điều này sẽ làm suy giảm đáng kể `yield` mạch và hiệu năng linh kiện. Mặc dù oxide mọc là vô định hình, nó có trật tự tầm ngắn (`short range order`), được minh họa trong **Hình 6.5**. Các tứ diện `SiO₄` là các đơn vị cơ bản mà `SiO₂` được tạo thành. Các tứ diện này liên kết với nhau bằng cách chia sẻ các nguyên tử oxy như minh họa ở bên phải của hình. Các nguyên tử chia sẻ như vậy được gọi là các nguyên tử oxy cầu nối (`bridging oxygen atoms`). Trong các dạng vô định hình của `SiO₂` cũng có thể có một số nguyên tử oxy không cầu nối (`non-bridging oxygen atoms`) hiện diện. Các dạng này thường được gọi là `fused silica`. Các dạng tinh thể của `SiO₂` như thạch anh (`quartz`) chỉ chứa các liên kết oxy cầu nối. Các dạng tinh thể và vô định hình khác nhau của `SiO₂` phát sinh vì khả năng của các liên kết oxy cầu nối quay cho phép vị trí của một tứ diện di chuyển so với các tứ diện lân cận. Chính sự quay tương tự này cho phép vật liệu mất trật tự tầm dài và do đó trở nên vô định hình. Ở các nhiệt độ xử lý thông thường, dạng nhiệt động ổn định của `SiO₂` là một trong các dạng tinh thể. Các dạng này hiếm khi được quan sát trong các cấu trúc `IC`, tuy nhiên, vì thời gian cần để `SiO₂` vô định hình tự sắp xếp lại thành dạng tinh thể rất dài so với các chu kỳ khuếch tán, oxy hóa hoặc ủ thông thường. Đôi khi các ống lò `fused silica` được sử dụng trong các lò oxy hóa hoặc khuếch tán sẽ kết tinh (một quá trình gọi là khử thủy tinh hóa, `devitrification`) sau nhiều tháng hoặc nhiều năm ở nhiệt độ cao.

---

**Hình 6.5:** Cấu trúc của kính `fused silica`. Các nguyên tử silicon nằm ở tâm của mỗi tứ diện. Khoảng cách `O-O` là `0,262 nm`; khoảng cách `Si-O` là `0,162 nm`. Khoảng cách liên kết `Si-Si` phụ thuộc vào dạng cụ thể của `SiO₂`, nhưng khoảng `0,31 nm`. Cấu trúc vòng sáu thành viên của `SiO₂` được trình bày theo khái niệm ở bên phải.

---

Các lớp oxide mọc trên `Si` thường ở trạng thái ứng suất nén (`compressive stress`). Tại mặt tiếp xúc `Si/SiO₂`, oxide đang mọc chỉ có thể giãn nở lên phía trên, không theo chiều ngang vì nó phải bám vào đế silicon. Điều này dẫn đến các ứng suất nén có thể lên đến `5 × 10⁹ dyne cm⁻²`. Ở nhiệt độ trên khoảng `1000°C`, oxide có thể giải phóng một phần ứng suất này bằng dòng chảy nhớt (`viscous flow`); ở nhiệt độ thấp hơn, độ nhớt của oxide quá cao để cho phép giải phóng đáng kể. Ngoài các ứng suất nội tại này có thể hiện diện sau khi một oxide được mọc, còn có sự chênh lệch lớn về hệ số giãn nở nhiệt giữa `Si` và `SiO₂`. Khi các wafer nguội đi sau khi một oxide được mọc, điều này dẫn đến một ứng suất nén bổ sung trong oxide có thể lên đến vài `× 10⁹ dyne cm⁻²`. Hai hiệu ứng này đặt đế silicon vào trạng thái căng (`tension`); tuy nhiên, đế dày hơn nhiều lần so với lớp oxide và kết quả là các ứng suất căng được giảm theo tỷ lệ chiều dày. Các hiệu ứng này có thể dễ dàng quan sát ngay cả trên các wafer silicon phẳng. Sau khi oxy hóa, `SiO₂` thường hiện diện ở cả bề mặt trên lẫn bề mặt sau của wafer và các ứng suất từ hai màng oxide do đó cân bằng nhau. Tuy nhiên, nếu oxide được tẩy hóa học từ một bề mặt, một sự cong rõ ràng sẽ được quan sát trong wafer vì các ứng suất. Trên thực tế, phép đo "độ cong wafer" (`wafer curvature`) này là một cách để xác định mức ứng suất trong `SiO₂` hoặc các màng mỏng khác trên các đế silicon.

**Hình 3.15** đã trình bày một ảnh kính hiển vi điện tử truyền qua độ phân giải cao (`TEM`) của mặt tiếp xúc `Si/SiO₂`. Độ phân giải nguyên tử trong ảnh này cho thấy rõ ràng cấu trúc tinh thể silicon, lớp `SiO₂` vô định hình và sự đột ngột của mặt tiếp xúc. Một số nghiên cứu gần đây sử dụng `TEM` và các kỹ thuật khác đã chỉ ra rằng mặt tiếp xúc `Si/SiO₂` thường được đặc trưng bởi một vùng chuyển tiếp rất hẹp (có lẽ chỉ một khoảng cách nguyên tử). Mặt tiếp xúc thường khá phẳng, mặc dù có các bậc một khoảng cách nguyên tử xảy ra đôi khi. Sự đột ngột của mặt tiếp xúc phụ thuộc ở một mức độ nào đó vào các điều kiện quy trình được sử dụng để mọc oxide, và mặt tiếp xúc hơi gồ ghề hơn đối với các oxide được mọc nhanh chóng (oxy hóa bằng `H₂O` so với `O₂` hoặc oxy hóa áp suất cao, ví dụ). Mặt tiếp xúc cũng hơi gồ ghề hơn đối với các oxide được mọc ở nhiệt độ thấp.

Động học mọc của các lớp `SiO₂` trên silicon đã được nghiên cứu trong hơn ba thập kỷ, và tiếp tục được nghiên cứu ngày nay. Các nghiên cứu đầu tiên khác nhau báo cáo tốc độ mọc có sự phụ thuộc tuyến tính, parabol, logarithm, logarithm nghịch đảo hoặc theo luật lũy thừa vào thời gian. Mô hình đầu tiên được chấp nhận rộng rãi về động học mọc là do Deal và Grove năm `1965` `[6.6]`. Công trình này chỉ ra rằng trên một dải điều kiện rộng, sự mọc tuân theo một quy luật tuyến tính-parabol có thể được giải thích trên cơ sở lý thuyết vững chắc. Các công trình sau đó nhìn chung tập trung vào việc mô hình hóa các điều kiện mọc mà đối với đó mô hình Deal-Grove không đủ. Các ví dụ bao gồm các oxide rất mỏng, oxide mọc trong môi trường hỗn hợp, oxide mọc trên các bề mặt silicon `2D` hoặc `3D`, và oxide mọc trên các đế pha tạp nặng. Chúng ta sẽ thảo luận về các mô hình này và các mô hình khác ở phần sau trong chương này.

Cũng đã có trong nhiều năm một cuộc tranh luận đáng kể về các chất oxy hóa nào khuếch tán qua `SiO₂` để mọc các lớp oxide mới. Trong pha khí phía trên wafer, các chất phân tử (`O₂` hoặc `H₂O`) hiện diện. Tuy nhiên, các chất này có thể phân ly hoặc thậm chí ion hóa để tạo thành `O`, `O⁻`, `O₂⁻` hay nhiều chất khác khi chúng đi vào `SiO₂`. Một số công trình đầu tiên `[6.2]` sử dụng điện trường gợi ý rằng một chất tích điện là chất khuếch tán chi phối. Tuy nhiên, các công trình sau đó phần lớn đã bác bỏ các kết quả này và ngày nay hầu hết các nhà nghiên cứu tin rằng `O₂` và `H₂O` trung hòa và/hoặc `OH` là các chất chính liên quan đến quá trình oxy hóa.

Các tính chất điện của mặt tiếp xúc `Si/SiO₂` đã được nghiên cứu chuyên sâu trong hơn `40` năm. Rất nhiều kiến thức đã được tích lũy về các tính chất này, cách chúng phụ thuộc vào các điều kiện quy trình và cách kiểm soát chúng. Ở bậc thứ nhất, mặt tiếp xúc là hoàn hảo. Mật độ của các khuyết tật hiện diện trong các linh kiện hiện đại vào cỡ `10⁹ - 10¹¹ cm⁻²` so với mật độ nguyên tử bề mặt silicon khoảng `10¹⁵ cm⁻²`. Hầu hết các khuyết tật tồn tại thường được quy cho các nguyên tử `Si` bị oxy hóa không hoàn toàn hoặc các nguyên tử `Si` có các liên kết không được thỏa mãn (`dangling bonds`). Tuy nhiên, chỉ khoảng `1` nguyên tử trong `10⁵` có khuyết tật như vậy.

Năm `1980`, trong một nỗ lực thống nhất nghiên cứu trong lĩnh vực này, Deal `[6.7]` đề xuất danh pháp được trình bày trong **Hình 6.6** để đại diện cho các loại khuyết tật điện khác nhau được tìm thấy thực nghiệm tại mặt tiếp xúc `Si/SiO₂` và trong các lớp `SiO₂`. Có bốn loại khuyết tật hay điện tích cơ bản tồn tại. Loại thứ nhất, `Qf`, được gọi là điện tích oxide cố định (`fixed oxide charge`). Thực nghiệm chúng ta thấy rằng một tấm điện tích dương (thường `10⁹ - 10¹¹ cm⁻²`) tồn tại trong oxide, rất gần mặt tiếp xúc. Nó dường như được định vị trong vòng `2 nm` của mặt tiếp xúc (có lẽ gần hơn) và có khả năng gắn với sự chuyển tiếp từ `Si` sang `SiO₂`. Hầu hết các giải thích vật lý cho `Qf` gợi ý rằng nó là do các nguyên tử `Si` bị oxy hóa không hoàn toàn có điện tích dương thực. `Qf` được gọi là điện tích oxide cố định vì trạng thái điện tích của nó không thay đổi trong quá trình hoạt động bình thường của linh kiện. Nó dương và bất biến trong các điều kiện thông thường.

Loại khuyết tật tích điện thứ hai hiện diện tại mặt tiếp xúc `Si/SiO₂` là `Qit`, điện tích bẫy mặt tiếp xúc (`interface trapped charge`). Nguồn gốc vật lý của các điện tích này thường được gợi ý là tương tự như `Qf`. Tức là, `Qit` nhiều khả năng là do một số loại nguyên tử silicon bị oxy hóa không hoàn toàn với các liên kết không được thỏa mãn hay `dangling bonds` nằm trong oxide nhưng rất gần mặt tiếp xúc. Tuy nhiên, có một sự khác biệt rất quan trọng giữa `Qit` và `Qf`. Điện tích gắn với `Qf` là cố định và dương. Điện tích gắn với `Qit` có thể dương, trung hòa hoặc âm, và trên thực tế có thể thay đổi trong quá trình hoạt động bình thường của linh kiện do việc bắt giữ các lỗ trống hoặc electron. Do đó có tên bẫy (`trap`) gắn với `Qit`. Các bẫy này hoạt động rất giống các bẫy mức sâu trong khối mà chúng ta đã thảo luận trong Chương `1` và `4` (**Hình 1.27**). Các mức năng lượng gắn với `Qit` tồn tại xuyên suốt vùng cấm, mặc dù thường có nhiều bẫy hơn ở các mức năng lượng gần các mép vùng dẫn và vùng hóa trị so với ở giữa vùng cấm. Việc oxy hóa một bề mặt silicon thường dẫn đến mật độ `Qit` vào cỡ `10⁹ - 10¹¹ cm⁻² eV⁻¹`, xấp xỉ cùng mật độ như tìm thấy đối với `Qf`. Trên thực tế, thường là trường hợp một quy trình dẫn đến giá trị cao của `Qf` cũng sẽ dẫn đến mật độ cao của `Qit`. Sự tương quan này là một trong các kết quả thực nghiệm gợi ý nguồn gốc chung cho hai điện tích.

**Hình 6.6:** Các điện tích gắn với hệ `SiO₂/Si`. (Theo Deal `[6.7]`).

---

Hai loại điện tích còn lại được trình bày trong **Hình 6.6** thường ít quan trọng hơn ngày nay. `Qm` là điện tích oxide di động (`mobile oxide charge`) có thể nằm ở bất kỳ đâu trong oxide, và là một vấn đề nghiêm trọng vào những năm `1960`. Vào thời điểm đó, thường xảy ra trường hợp các cấu trúc `MOS` không ổn định sau khi chế tạo. Chúng ta đã thảo luận ngắn gọn về điều này trong Chương `1` và lại trong Chương `4`, và đã quan sát thấy rằng sự không ổn định trong điện áp ngưỡng transistor (`VTH`) này được truy nguyên đến sự hiện diện của các ion di động như `Na⁺` và `K⁺` trong các oxide cổng — tức `Qm`. Với sự chú ý đúng mức đến việc vệ sinh trong các cơ sở chế tạo wafer, vấn đề này phần lớn đã biến mất vào những năm `1970`, mặc dù ngay cả ngày nay đôi khi nó vẫn trở thành vấn đề trong các cơ sở sản xuất vì các nồng độ `ppm` của các ion di động này có thể gây ra các sự không ổn định đo được. Trong ví dụ chúng ta xem xét ở Chương `4`, chúng ta đã thấy rằng sự dịch chuyển trong `VTH` của các linh kiện `MOS` gây ra bởi `Na⁺` hoặc `K⁺` tỷ lệ nghịch với `COX` (Phương trình `4.1`). Do đó, khi chiều dày oxide cổng được thu nhỏ, các giá trị `Qm` lớn hơn có thể được chấp nhận.

`Qot` hay điện tích bẫy oxide (`oxide trapped charge`), cũng có thể nằm ở bất kỳ đâu trong oxide, là loại điện tích quan sát được thực nghiệm cuối cùng trong hệ `Si/SiO₂`. Các khuyết tật này nhiều khả năng là các liên kết `Si-O` bị đứt trong khối oxide, xa mặt tiếp xúc `Si/SiO₂`. Các liên kết như vậy có thể bị đứt bởi bức xạ ion hóa hoặc bởi một số bước quy trình được sử dụng trong chế tạo `IC` ngày nay. Khắc plasma, ví dụ, làm lộ các oxide với các ion, electron và các chất trung hòa có năng lượng cao. Cấy ion thường được thực hiện qua một lớp oxide. Các quá trình này và các quá trình khác có thể làm hỏng các oxide dẫn đến các bẫy trong oxide khối — `Qot`. Các bẫy như vậy thường được sửa chữa bằng một lần ủ nhiệt độ cao trước khi chế tạo linh kiện hoàn tất, cho phép các liên kết bị đứt tự sửa chữa. Nếu chúng tồn tại trong oxide vì không được ủ hoàn toàn, hoặc vì linh kiện bị tiếp xúc với bức xạ ion hóa, các bẫy này có thể bắt giữ các lỗ trống hoặc electron có thể bị phun vào oxide trong quá trình hoạt động của linh kiện, dẫn đến điện tích bị bẫy. Do đó có tên `Qot`.

`Qot` đã trở nên ngày càng quan trọng hơn trong những năm gần đây do các điện trường cao hiện diện trong các linh kiện được thu nhỏ. Các điện trường cao hơn này dẫn đến các hạt tải "nóng" (`hot carriers`) có năng lượng cao hơn, có thể đạt đến năng lượng đủ cao để được phun vào các oxide cổng của các linh kiện `MOS` hiện đại. Nếu các bẫy oxide hiện diện, hoặc nếu chúng được tạo ra bởi chính các hạt tải có năng lượng cao, sự bẫy điện tích có thể xảy ra. Điều này dẫn đến sự dịch chuyển ngưỡng của linh kiện theo thời gian (xem Phương trình `4.1`) và các lo ngại về độ tin cậy. Một thước đo phổ biến về chất lượng của một chất cách điện cổng là `QBD` hay lượng điện tích có thể được truyền qua oxide trước khi xảy ra sự cố (đánh thủng). Sự bẫy điện tích trong các chất cách điện `SiO₂` cũng là một vấn đề lớn trong các linh kiện có thể lập trình như `EPROM` trong đó dòng điện có chủ đích đi qua oxide cổng như một phần của hoạt động ghi.

Cả bốn loại điện tích trong **Hình 6.6** đều có thể có tác hại đến hoạt động của linh kiện. Kết quả là, sự chú ý đặc biệt thường được thực hiện trong quá trình chế tạo để chọn các chuỗi quy trình sẽ giảm thiểu các điện tích này. Nói chung, điều này được thực hiện bằng các lần ủ trơ nhiệt độ cao trong `Ar` hoặc `N₂` về cuối của `process flow`, và bằng một lần ủ nhiệt độ vừa phải cuối cùng (`≈ 400°C`) trong `H₂` hoặc khí tạo hình (`forming gas`, `N₂/H₂`) ở cuối quy trình. Chúng ta sẽ thảo luận về các lần ủ và điện tích này cẩn thận hơn trong Mục `6.5.13` ở phần sau trong chương này.

Một điểm cuối cùng liên quan đến các lớp `SiO₂` trên `Si` là quan trọng. Một trong những ứng dụng sớm nhất và quan trọng nhất của các lớp `SiO₂` là để che chắn chống lại sự khuếch tán tạp chất. Các oxide vẫn còn được sử dụng rộng rãi cho mục đích này ngày nay và ứng dụng này về cơ bản phụ thuộc vào thực tế là hầu hết các tạp chất có hệ số khuếch tán thấp hơn nhiều trong `SiO₂` so với trong `Si`. Tính toán chiều dày của một lớp oxide cần thiết để che chắn thành công chống lại một hoạt động khuếch tán hoặc cấy ion là tương đối đơn giản. Tuy nhiên, chúng ta sẽ hoãn thảo luận về các điểm này cho đến Chương `7` và `8` nơi chúng ta thảo luận về khuếch tán và cấy ion chi tiết.

Phụ lục chứa một số tính chất hữu ích và quan trọng của ba chất cách điện thường được sử dụng trong công nghệ silicon. `SiOₓNᵧ` là một chất cách điện thường được hình thành bằng cách làm lộ một lớp `SiO₂` với `NH₃` hoặc môi trường chứa nitơ khác để chuyển đổi oxide thành oxynitride. Các tính chất của cả oxynitride lẫn `Si₃N₄` thay đổi phần nào với các điều kiện lắng đọng và/hoặc nitride hóa và sẽ được thảo luận chi tiết hơn trong Mục `6.5.11` và ở cuối chương khi các xu hướng tương lai được thảo luận.

---

## 6.3 Các phương pháp và thiết bị sản xuất

Các hệ thống oxy hóa là một trong những loại thiết bị xử lý bán dẫn đơn giản nhất. Về mặt khái niệm, tất cả những gì cần thiết, như minh họa trong **Hình 6.7**, là một lò có khả năng đạt nhiệt độ từ `600 - 1200°C` và một hệ phân phối khí đơn giản có khả năng đưa `O₂` hoặc `H₂O` vào. Trong thực tế, các hệ thống như vậy phức tạp hơn nhiều do nhu cầu đồng đều, có thể tái tạo và sạch trong quy trình. Các lò hiện đại có khả năng xử lý đến vài trăm wafer `8"`, với độ đồng đều nhiệt độ `±0,5°C`.

Hầu hết các hệ thống như vậy đang sử dụng ngày nay có hướng nằm ngang với chất oxy hóa được đưa vào ở đầu sau và các wafer ở đầu trước. Nhiều lò mới được phát triển gần đây có hướng thẳng đứng vì chúng chiếm ít diện tích sàn hơn trong một cơ sở sản xuất. Các nguồn lỏng của `O₂` và `H₂` thường được sử dụng, với các bồn chứa nằm bên ngoài cơ sở sản xuất. Các khí từ các nguồn lỏng này được dẫn đến các lò qua các đường ống thép không gỉ độ tinh khiết cao. Đối với các oxy hóa bằng `O₂`, oxy được đưa trực tiếp vào lò. Đối với các oxy hóa bằng `H₂O`, `O₂` và `H₂` được đốt ở đầu sau của lò để tạo ra `H₂O`. Các đường nguồn bổ sung đến lò có thể cho phép `HCl` khí hoặc `TCA` (trichloroethane), cả hai đều cung cấp nguồn `Cl`. `Cl` có thể được sử dụng để làm sạch ống lò trước khi oxy hóa, hoặc thực sự có thể được sử dụng trong quá trình oxy hóa như một chất phụ gia tỷ lệ nhỏ. `Cl` phục vụ mục đích hữu ích là phản ứng với nhiều ion kim loại không mong muốn và tạo ra các sản phẩm phụ pha khí có thể được thải ra khỏi lò. (Nhớ lại thảo luận của chúng ta trong Chương `4` về các quy trình làm sạch. `HCl` là một thành phần của dung dịch làm sạch `SC-2`.) Nếu `HCl` hoặc `TCA` được sử dụng trong quá trình oxy hóa, một số `Cl` được kết hợp vào lớp `SiO₂` đang mọc. Điều này cung cấp một mức độ bảo vệ nào đó khỏi các lượng vết của các chất nhiễm bẩn ion như `Na⁺` và cũng thay đổi động học mọc. Chúng ta sẽ thảo luận các vấn đề này đầy đủ hơn sau này trong Mục `6.5.6`.

---

**Hình 6.7:** Hệ thống oxy hóa silicon theo khái niệm.

---

Các wafer thường được nạp vào lò trên các giá đỡ hoặc "thuyền" (`boats`) giữ `10 - 50` wafer. Các thuyền này được mang vào lò bởi các hệ thống nạp tự động thường là các cánh tay công xôn (`cantilever arms`) di chuyển chậm vào vùng nóng của lò. Các hệ thống oxy hóa nằm ngang đầu tiên sử dụng các xe trượt, đôi khi có bánh xe thạch anh được đẩy vào vùng nóng của lò. Tuy nhiên, các hệ thống như vậy chắc chắn khuấy động các hạt từ hệ thống lò có thể lắng đọng lên các wafer gây mất `yield`. Ngày nay, các hệ thống công xôn mang các wafer vào lò mà không thực sự chạm vào thành lò. Trong trường hợp các lò thẳng đứng, các thang máy được sử dụng để mang các wafer lên vào vùng nóng của lò.

Hệ thống kiểm soát nhiệt độ của lò đơn giản về mặt khái niệm. Lò thường được chia thành `3 - 5` vùng để kiểm soát nhiệt độ, với các wafer nằm ở phần trung tâm trong quá trình oxy hóa. Các vùng bên ngoài được thiết kế để giúp bù đắp cho sự mất nhiệt ra các đầu ống, để có thể duy trì một phần trung tâm dài với nhiệt độ đồng đều. Các cặp nhiệt điện (`thermocouples`) theo dõi nhiệt độ ở mỗi phần và một bộ điều khiển cung cấp điện cho các phần tử gia nhiệt điện trở ở mỗi phần để duy trì biên dạng nhiệt độ phẳng trong vùng trung tâm. Để tránh các gradient nhiệt lớn trên các wafer, vốn có thể gây ra các khuyết tật tinh thể học, các wafer thường được nạp ở nhiệt độ vừa phải (khoảng `800°C`) và lò sau đó được tăng lên đến nhiệt độ oxy hóa sau khi các wafer đã ở trong vùng nóng trung tâm. Bộ điều khiển lò thường được thiết kế để kiểm soát tốc độ tăng và tốc độ giảm nhiệt độ để ứng suất nhiệt trên các wafer được giảm thiểu. Tốc độ tăng/giảm vào cỡ `1°C s⁻¹` là điển hình.

Ở `1000°C`, tốc độ oxy hóa trong `H₂O` vào cỡ `0,1 nm s⁻¹` và xấp xỉ tăng gấp đôi khi nhiệt độ tăng `100°C`. Kết quả là, kiểm soát nhiệt độ ở mức `±0,5°C` và kiểm soát thời gian ở mức giây là cần thiết để tạo ra các chiều dày oxide nhất quán từ lô này sang lô khác.

Phần lớn các lò oxy hóa ngày nay hoạt động ở áp suất khí quyển vì đây là những lò đơn giản nhất để vận hành. Tuy nhiên, chúng ta sẽ thấy trong Mục `6.5.3` rằng tốc độ mọc oxide tỷ lệ thuận với áp suất chất oxy hóa (ở bậc thứ nhất), vì vậy có thể mọc một chiều dày oxide nhất định trong thời gian ngắn hơn ở áp suất cao. Các hệ thống như vậy tồn tại ngày nay và được sử dụng trong các ứng dụng trong đó một oxide nhiệt dày phải được mọc với ngân sách nhiệt (`Dt`) tối thiểu. Áp suất thấp hơn khí quyển đơn giản để thu được bằng cách pha loãng khí oxy hóa với khí trơ như `Ar` hoặc `N₂`. Trong trường hợp này, tốc độ oxy hóa bị làm chậm lại, xấp xỉ theo tỷ lệ với áp suất riêng phần chất oxy hóa.

Một chủ đề cuối cùng cần được đề cập ngắn gọn trước khi chúng ta rời phần này. Nỗ lực tiếp tục giảm kích thước các linh kiện `VLSI` trong những năm gần đây đã đòi hỏi các bước nhiệt độ cao rất ngắn. Ngoài ra, các oxide cổng trong các linh kiện `MOS` hiện đại dày `< 10 nm`, đòi hỏi các chu trình mọc ngắn và được kiểm soát tốt. Các vấn đề này đã dẫn đến việc nghiên cứu các kỹ thuật Oxy hóa Nhiệt Nhanh (`Rapid Thermal Oxidation`, `RTO`) để mọc các lớp `SiO₂` rất mỏng. Thông thường, các hệ thống `RTO` sử dụng một buồng được gia nhiệt bằng đèn có thể đưa một wafer lên nhiệt độ oxy hóa với tốc độ `100°C s⁻¹`, giữ wafer ở đó trong khi oxide được mọc, và sau đó làm mát trở lại về nhiệt độ phòng, cũng chỉ trong vài giây. Thường các hệ thống như vậy là các máy xử lý wafer đơn lẻ (`single wafer`). Khi các báo cáo đầu tiên về động học mọc oxide `RTO` bắt đầu xuất hiện trong tài liệu, có những gợi ý rằng động học mọc khác với những gì quan sát được trong các lò oxy hóa và rằng các mô hình mới sẽ cần thiết để giải thích động học. Điều này có thể đúng, ví dụ, nếu các hiệu ứng quá độ, vốn không đáng kể trong một lò mất `15` phút để nung nóng các wafer, trở nên quan trọng khi hằng số thời gian của hệ thống được đo bằng giây. Tuy nhiên, hiện nay có vẻ như các mô hình thông thường thực ra có thể thỏa đáng. Một trong những vấn đề rất khó trong một hệ thống `RTO` là biết chính xác nhiệt độ wafer thực sự là bao nhiêu. Các hệ thống này thường đỡ wafer trên một khối lượng nhiệt nhỏ để có thể nung nóng wafer nhanh chóng. Điều này làm cho việc sử dụng cặp nhiệt điện để đo nhiệt độ như trong lò rất khó khăn. Các kỹ thuật khác như sử dụng đầu đo nhiệt hỏa tiễn (`pyrometer`) thường được sử dụng, nhưng các phương pháp này có những vấn đề riêng của chúng. Kết quả là, một số thí nghiệm `RTO` đầu tiên gợi ý "động học mới" có thể đã làm vậy do sự không chắc chắn hoặc biến thiên về nhiệt độ wafer. Các công việc bổ sung trong tương lai sẽ làm rõ liệu các hiệu ứng quá độ có hay không đòi hỏi bổ sung vào các mô hình oxy hóa tiêu chuẩn.

Một số lò oxy hóa ngày nay có khả năng "tăng nhiệt nhanh" (`fast ramp`, `≈ 10°C s⁻¹`) cung cấp khả năng trung gian giữa các lò thông thường và các hệ thống `RTO`. Các lò mới này cung cấp kiểm soát nhiệt độ rất tốt thông qua việc sử dụng các cặp nhiệt điện thông thường để đo nhiệt độ, cùng với tốc độ tăng nhiệt nhanh phù hợp với các chu trình `Dt` ngắn hơn và kiểm soát tốt hơn các oxide mỏng.

---

## 6.4 Các phương pháp đo

Các phép đo thực nghiệm về kết quả của một quy trình oxy hóa là một phần thiết yếu của bất kỳ quy trình sản xuất nào. Các tham số quan tâm đối với một lớp oxide (hoặc điện môi khác) thường là chiều dày, hằng số điện môi, chiết suất, độ bền điện môi và mật độ khuyết tật. Độ đồng đều của tất cả các tham số này trên một wafer và từ wafer này sang wafer khác cũng quan trọng.

Các kỹ thuật đo có sẵn có thể được phân loại rộng thành ba nhóm. Nhóm thứ nhất liên quan đến các phép đo vật lý thường phá hủy mẫu. Nhóm thứ hai liên quan đến các kỹ thuật quang học có thể đo một số nhưng không phải tất cả các tham số quan tâm. Chúng thường không phá hủy. Nhóm thứ ba của các phép đo liên quan đến các phép đo điện. Các phép đo này cũng thường không phá hủy và về mặt tiềm năng là mạnh mẽ nhất vì chúng đo trực tiếp các tham số quan tâm trong các linh kiện điện.

---

### 6.4.1 Phép đo vật lý

Trong một trong những phép đo vật lý đơn giản nhất, chất điện môi được khắc bỏ ở một số vùng sử dụng một chất ăn mòn hóa học tấn công màng mỏng nhưng không tấn công đế bên dưới (`HF` đối với một lớp `SiO₂`). Một mũi dò kim nhỏ sau đó được di chuyển qua bậc bề mặt tương ứng với cạnh khắc của màng. Việc khuếch đại cơ học hoặc điện tín hiệu nhỏ tạo ra một phép đo chiều cao bậc. Các thiết bị kiểu này đã có sẵn thương mại trong nhiều năm và có độ phân giải dưới `10 nm`. Sự phát triển gần đây của kính hiển vi đường hầm quét (`STM`), kính hiển vi lực nguyên tử (`AFM`) và các thiết bị phái sinh đã đẩy độ phân giải của các công cụ kiểu "mũi dò" này đến kích thước nguyên tử. **Hình 1.3** đã trình bày một ví dụ về khả năng của các thiết bị này. Các kỹ thuật vật lý khác để đo chiều dày màng bao gồm các ảnh `SEM` mặt cắt ngang tương tự **Hình 6.4** có thể tạo ảnh chiều dày màng, hoặc các ảnh mặt cắt ngang `TEM` độ phân giải cao hơn như được trình bày trong **Hình 3.15**. Tất cả các kỹ thuật này đòi hỏi chuẩn bị mẫu và do đó không phù hợp lắm cho các phép đo trong quy trình trên một dây chuyền sản xuất. Chúng cũng chỉ cung cấp thông tin về chiều dày màng.

---

### 6.4.2 Phép đo quang học

Các kỹ thuật quang học được sử dụng rất rộng rãi để đo chiều dày màng và một số thiết bị sẵn có thương mại. Nhiều thiết bị phụ thuộc vào phép đo ánh sáng phản xạ từ mẫu như minh họa trong **Hình 6.8**. Nếu ánh sáng đơn sắc bước sóng `λ` chiếu lên bề mặt mẫu ở góc `φ`, một phần ánh sáng sẽ được phản xạ trực tiếp. Nếu lớp `xO` trong suốt, một phần ánh sáng cũng sẽ phản xạ từ mặt tiếp xúc dưới. Đối với một số giá trị `λ`, hai sóng phản xạ sẽ đồng pha và cộng lại; đối với các giá trị `λ` khác, giao thoa hủy sẽ xảy ra. Kết quả là cường độ ánh sáng phản xạ sẽ đi qua các cực tiểu và cực đại khi `λ` thay đổi. Các hiệu ứng này hoàn toàn giống với các hiệu ứng gây ra sóng dừng trong quá trình phơi `photoresist`. (Nhớ lại các **Hình 5.23** và **5.24**.) Các cực đại và cực tiểu xảy ra tại các giá trị `λ` được cho bởi

---

> **[Công thức toán]**
>
> $$
> \lambda_{min,max} = \frac{2n_1 x_O \cos\beta}{m}
> \tag{6.1}
> $$
>
> trong đó:
>
> $$
> \beta = \sin^{-1}\!\left[\frac{n_O \sin\phi}{n_1}\right]
> \tag{6.2}
> $$

---

và `m = 1, 2, 3,...` cho các cực đại và `1/2, 3/2, 5/2,...` cho các cực tiểu. Đây đơn giản là các phiên bản tổng quát của tính tuần hoàn đơn giản mà chúng ta đã sử dụng cho các sóng dừng trong `photoresist` ở Chương `5`, đối với ánh sáng chiếu thẳng đứng. Các thiết bị thương mại sử dụng quang phổ kế (`spectrophotometers`) để quét bước sóng chiếu với `φ` không đổi. Chúng sau đó đo chiều dày màng điện môi bằng cách khớp cường độ phản xạ thu được với Phương trình `6.1`. Kỹ thuật này hoạt động đáng tin cậy đối với các chiều dày màng lớn hơn vài chục `nm`. Đối với các màng mỏng hơn, khó phát hiện cực tiểu đầu tiên trừ khi sử dụng ánh sáng bước sóng rất ngắn. Khi sử dụng kỹ thuật này, chiết suất của màng điện môi phải được biết vì nó xuất hiện trực tiếp trong Phương trình `6.1`.

---

**Hình 6.8:** Sự phản xạ ánh sáng từ một mẫu có một màng mỏng trong suốt trên bề mặt của nó. `nO` là chiết suất của không khí (`1,0`), `n₁` là chiết suất của màng mỏng và `n₂` là chiết suất của đế. `φ` là góc của ánh sáng chiếu, `β` là góc của ánh sáng phản xạ tại mặt tiếp xúc dưới.

---

Có nhiều trường hợp quan tâm trong công nghệ silicon trong đó các màng điện môi mỏng hơn vài chục nm cần được đo, hoặc trong đó hằng số điện môi của màng không được biết chính xác. Các ví dụ bao gồm các oxide cổng trong các cấu trúc `MOS` hiện nay dưới `10 nm` về chiều dày và các màng `Si₃N₄` hoặc `SiOₓNᵧ` trong đó `n₁` có thể thay đổi theo các điều kiện xử lý. Đối với các ứng dụng này, đo elip (`ellipsometry`) là một phương pháp tốt hơn để đo các tính chất màng. Về mặt khái niệm, đo elip hoạt động theo cách tương tự như kỹ thuật phản xạ được mô tả ở trên. Tuy nhiên, ánh sáng phân cực được sử dụng trong máy đo elip và sự thay đổi trong phân cực khi ánh sáng được phản xạ từ mặt tiếp xúc điện môi/đế được đo. Nói chung, sự thay đổi trong phân cực phụ thuộc vào các tính chất của cả màng lẫn đế. Tuy nhiên, trong trường hợp đơn giản khi các tính chất quang học của đế được biết và màng trong suốt ở các bước sóng đang được sử dụng, sự thay đổi trong phân cực của ánh sáng phản xạ chỉ phụ thuộc vào chiều dày màng và chiết suất. Các máy đo elip thương mại sẵn có có thể dễ dàng đo các màng xuống `1 nm` chiều dày và xác định chính xác chiết suất. Thường các thiết bị này được điều khiển bằng máy tính để các tính chất màng được tính toán tự động.

Cho đến nay, kỹ thuật quang học đơn giản nhất để đánh giá chiều dày màng điện môi là sử dụng các biểu đồ màu (`color charts`). Các biểu đồ này ban đầu được mô tả bởi Pliskin và Conrad `[6.8]` và dựa trên ý tưởng rằng nếu ánh sáng trắng được dùng để chiếu sáng một màng điện môi trong suốt mỏng trên một đế phản xạ (như trong **Hình 6.8**), giao thoa hủy sẽ xảy ra đối với một số bước sóng trong ánh sáng phản xạ, cho ánh sáng phản xạ một màu đặc trưng. Điều này cho phép quan sát đơn giản màu sắc của lớp oxide hoặc nitride để ước lượng chiều dày màng. Các bảng trong Phụ lục cung cấp các màu này cho các màng `SiO₂` hoặc `Si₃N₄` trên các đế phản xạ (thường là silicon). Các biểu đồ giả sử rằng các màng đang được quan sát vuông góc dưới ánh sáng huỳnh quang ánh ngày (`daylight fluorescent lighting`). Các màu lặp lại khoảng mỗi `300 nm` đối với `SiO₂` và khoảng mỗi `200 nm` đối với `Si₃N₄`. Vì lý do này, các tiêu chuẩn thường được sử dụng kết hợp với các biểu đồ này. Nếu mẫu đang khảo sát được xem cạnh nhau với một tiêu chuẩn có cùng màu, và người quan sát sau đó nhìn cả hai ở một góc, màu sắc của cả hai sẽ thay đổi khi góc nhìn thay đổi. Màu sắc sẽ thay đổi trên cả hai theo cùng một cách, chỉ khi các chiều dày thực sự giống nhau. Điều này cho phép phân biệt mẫu cụ thể phù hợp ở đâu trên biểu đồ màu. Mắt người đặc biệt giỏi phân biệt màu sắc và ước lượng chiều dày màng trong khoảng `10 - 20 nm` có thể được thực hiện với các biểu đồ này, đặc biệt nếu cũng có sẵn các tiêu chuẩn. Các khoảng được bao phủ bởi các biểu đồ này là những khoảng thường gặp trong công nghệ silicon. Tuy nhiên, lưu ý rằng các oxide mỏng hơn khoảng `50 nm` không có màu đặc trưng nào, vì vậy phương pháp này không hữu ích trong khoảng chiều dày này.

### 6.4.3 Phép đo điện — Tụ điện MOS

Loại kỹ thuật đo thứ ba là các kỹ thuật liên quan đến phép đo điện. Đây là các phương pháp về mặt tiềm năng mạnh mẽ nhất vì chúng đo các tham số có tầm quan trọng trực tiếp đối với các linh kiện bán dẫn — các điện dung, các điện tích điện v.v. Cho đến nay, kỹ thuật điện chi phối nhất là phương pháp điện dung-điện áp hay `CV`. Kỹ thuật này được sử dụng rất rộng rãi và cung cấp một lượng lớn thông tin về các màng điện môi và các mặt tiếp xúc mà các màng đó tạo ra với các chất bán dẫn bên dưới. Chúng ta sẽ mô tả cách kỹ thuật này hoạt động và thông tin mà nó cung cấp trong các đoạn sau. Chúng ta sẽ áp dụng kỹ thuật `CV` trong chương này để giúp hiểu các tính chất của mặt tiếp xúc `Si/SiO₂`. Trong các Chương sau (đặc biệt là `7` và `8`), chúng ta sẽ áp dụng nó để đo các biên dạng pha tạp trong chất bán dẫn.

Cấu trúc cơ bản được sử dụng để thực hiện các phép đo `CV` là tụ điện `MOS`, bao gồm một đế bán dẫn, một lớp điện môi và một điện cực dẫn điện. Chúng ta đã xem xét ngắn gọn cấu trúc này trong Chương `4` (các Hình `4.15` và `4.19`) trong mối liên hệ với các phép đo đánh thủng điện môi và thời gian sống hạt tải. Vì ứng dụng chính của tụ điện `MOS` là trong việc đặc trưng hóa và nghiên cứu các chất cách điện và mặt tiếp xúc `Si/SiO₂`, chúng ta sẽ thảo luận về cấu trúc này chi tiết hơn ở đây.

Nói chung, hệ `MOS` là (polysilicon hoặc `Al`)-`SiO₂`-`Si` mặc dù bất kỳ tổ hợp dẫn điện/chất cách điện/bán dẫn nào đều có thể được sử dụng. Phép đo cơ bản được minh họa trong **Hình 6.9** nơi chúng ta xét trường hợp cụ thể của cấu trúc kim loại/`SiO₂`/`Si` loại `N`. Hình này trình bày ba vùng hoạt động của tụ điện `MOS`. Các điện áp dương trên điện cực kim loại tương ứng với tích lũy (`accumulation`) (**Hình 6.9a**), các điện áp âm đầu tiên gây ra suy giảm (`depletion`) (**Hình 6.9b**) và sau đó là đảo chiều (`inversion`) (**Hình 6.9c**) trong đế. Chúng ta sẽ định nghĩa các thuật ngữ này chính xác hơn trong thời gian ngắn. Phần kim loại của cấu trúc thường được gọi là cổng (`gate`) vì đó là vai trò của nó trong một transistor `MOS` có cùng cấu trúc. Điều quan trọng cần lưu ý là điện áp cổng `VG` là điện áp `DC` và trong thảo luận sau đây được giả sử là được áp dụng đủ lâu để hệ đạt đến trạng thái ổn định cuối cùng. Chúng ta sẽ quay lại điểm này sau khi thảo luận về các đường cong `CV` tần số cao và tần số thấp cũng như các ứng dụng khác của kỹ thuật.

Chúng ta đưa ra thêm giả thiết rằng chất cách điện và mặt tiếp xúc chất cách điện/bán dẫn (`SiO₂/Si` trong trường hợp này) chỉ có số lượng nhỏ các điện tích hay khuyết tật. Nói cách khác, bốn loại điện tích được mô tả trong **Hình 6.6** được giả sử là có mật độ tương đối nhỏ. Nếu đây là trường hợp, các đường sức điện trường bắt đầu từ các điện tích trên cổng sẽ kéo dài qua chất cách điện và vào đế nơi có các điện tích dấu ngược chiều sẵn có để kết thúc các đường sức. Nếu có số lượng lớn điện tích hay khuyết tật trong chất cách điện hoặc tại mặt tiếp xúc chất cách điện/bán dẫn, các đường sức điện trường có thể kết thúc tại các điện tích này trước khi đến chất bán dẫn bên dưới. Kết quả là việc áp điện áp lên cổng sẽ có ít tác động đến chất bán dẫn. Suy giảm và đảo chiều không thể đạt được một cách có kiểm soát và cấu trúc sẽ không hữu ích trong các transistor `MOS`. Đây thực ra là điều xảy ra trong nhiều hệ chất cách điện/bán dẫn, nhưng hệ `SiO₂/Si` gần như là hoàn hảo về mặt điện.

---

**Hình 6.9:** Cấu trúc tụ điện `MOS` và đồ thị `C-V` thu được. a) tương ứng với tích lũy, b) với suy giảm và c) với đảo chiều.

---

Xét trước tiên trường hợp với điện áp `DC` là `+VG` trên cổng (**Hình 6.9a**). Vì đế loại `N`, các điện áp cổng dương sẽ hút các electron hạt tải đa số đến bề mặt silicon. Nếu bây giờ chúng ta đo điện dung tín hiệu nhỏ của cấu trúc bằng cách chồng một tín hiệu `AC` nhỏ lên `VG`, điện dung đo được sẽ đơn giản là điện dung oxide `Cox`. Đế silicon sẽ đóng vai trò đơn giản là một điện trở nối tiếp với `Cox` vì không có vùng suy giảm nào hình thành đối với các điện áp cổng dương. Phép đo chỉ trích xuất phần điện dung của trở kháng, phần này sẽ độc lập với `VG` như trình bày ở phần bên phải của **Hình 6.9a**. Các tần số trong khoảng `100 kHz` đến `1 MHz` thường được sử dụng cho phép đo này.

Bây giờ xét việc áp các điện áp cổng `DC` âm trong phần b) của hình. Các điện áp âm sẽ đẩy các electron hạt tải đa số ra khỏi bề mặt, tạo ra một vùng suy giảm. Bất kỳ điện tích âm nào chúng ta đặt lên cổng phải được cân bằng bởi một điện tích dương tương ứng trong đế để duy trì tính trung hòa điện. Điện tích dương được cung cấp bởi các nguyên tử donor trong đế có điện tích dương thực khi các electron di động bị đẩy ra xa khỏi bề mặt. Về mặt khái niệm, điều xảy ra là các electron bị đẩy ra khỏi vùng bề mặt chất bán dẫn chảy ra khỏi đáy của đế, qua nguồn điện được kết nối với cổng và sau đó đến cổng nơi chúng cung cấp điện tích cổng âm. Kết quả là,

---

> **[Công thức toán]**
>
> $$
> Q_G = Q_D = N_D x_D
> \tag{6.3}
> $$

---

trong đó `QG` và `QD` có đơn vị số điện tích `cm⁻²`, và `ND` là mức pha tạp trong đế được giả sử là đồng đều. Một vùng suy giảm sẽ hình thành đến độ sâu `xD`. Khái niệm ở đây rất giống với vùng suy giảm tiếp giáp `PN` mà chúng ta đã thảo luận trong Chương `1`. Vùng suy giảm sẽ có một điện dung trên một đơn vị diện tích gắn với nó được cho bởi

---

> **[Công thức toán]**
>
> $$
> C_D = \frac{\varepsilon_S}{x_D}
> \tag{6.4}
> $$

---

trong đó `εS` là hằng số điện môi của silicon. Tuy nhiên, `xD` là hàm số của điện áp cổng, tăng lên khi `VG` tăng. Điện dung tổng thể được đo cho cấu trúc bây giờ là `Cox` nối tiếp với một `CD` thay đổi. Đồ thị ở bên phải của **Hình 6.9b** phản ánh điều này, với điện dung giảm khi `VG` trở nên âm hơn vì `xD` tăng khi `VG` trở nên âm hơn.

Đối với các giá trị lớn hơn của điện áp cổng `DC` âm, bề mặt silicon thực sự sẽ "đảo chiều" từ loại `N` sang loại `P` (**Hình 6.9c**). Điện áp âm trên cổng sẽ hút các lỗ trống hạt tải thiểu số trong đế đến bề mặt và nếu đủ lỗ trống hiện diện ở đó, chúng có thể hình thành một lớp đảo chiều của các hạt tải loại `P`. Điện áp cổng mà điều này xảy ra được gọi là điện áp ngưỡng (`threshold voltage`) và chính xác là điện áp tương tự mà chúng ta đã thảo luận trong các chương trước trong mối liên hệ với việc bật một transistor `MOS`. Một khi lớp đảo chiều hình thành, `xD` ngừng mở rộng và đạt đến giá trị cực đại `xDMax`.

Đối với tất cả các vùng hoạt động của tụ điện, điện tích cổng phải được cân bằng bởi điện tích trong đế. Tức là

---

> **[Công thức toán]**
>
> $$
> Q_G = N_D x_D + Q_I
> \tag{6.5}
> $$

---

trong đó `QI` là mật độ điện tích (số điện tích trên `cm²`) trong lớp đảo chiều. `QI` không đáng kể trong điều kiện suy giảm nên `xD` mở rộng trong quá trình suy giảm để cân bằng `QG`. Tuy nhiên, một khi lớp đảo chiều hình thành, điện tích cổng bổ sung được cân bằng bởi `QI` thay vì `QD` nên `xD` đạt giá trị cực đại. Điều này có nghĩa là đường cong `CV` sẽ đạt cực tiểu như trình bày trong **Hình 6.9c**.

Để hiểu tại sao `QG` bổ sung được cân bằng bởi `QI` chứ không phải `QD` một khi đảo chiều xảy ra, chúng ta cần quay lại khái niệm giản đồ vùng mà chúng ta đã giới thiệu trong Chương `1`. **Hình 6.10** trình bày giản đồ vùng cho tụ điện `MOS` trong các điều kiện tích lũy, suy giảm và đảo chiều. Oxide ngăn bất kỳ dòng điện nào chảy qua cấu trúc, do đó chất bán dẫn ở trạng thái cân bằng và chúng ta có thể vẽ mức Fermi là phẳng trong silicon. Mức Fermi trong kim loại được tách khỏi `EF` trong silicon một lượng bằng điện áp cổng được áp. Trong **Hình 6.10a**, một điện áp cổng `DC` dương được áp (nhớ lại rằng chiều dương là hướng xuống trong các giản đồ này theo quy ước). Điều này sẽ gây ra sự cong xuống dưới của các vùng trong chất bán dẫn ở vùng gần bề mặt. Điều này đặt `EF` gần `EC` hơn tại bề mặt so với trường hợp trong khối xa khỏi bề mặt. Như chúng ta đã thấy trong Chương `1`, điều này có nghĩa là quần thể electron do đó cao hơn tại bề mặt so với trong khối. Điều này tích lũy các electron tại bề mặt, kết luận giống như chúng ta đã đạt được khi thảo luận **Hình 6.9a**.

---

**Hình 6.10:** Giản đồ vùng cho tụ điện `MOS` trong a) tích lũy, b) suy giảm và c) đảo chiều.

---

Trong **Hình 6.10b**, một điện áp cổng `DC` âm đã được áp, gây ra sự cong lên phía trên của các vùng trong chất bán dẫn gần bề mặt. Điều này tạo ra vùng suy giảm mà chúng ta đã thảo luận trong **Hình 6.9b** vì trên khoảng cách `xD`, `EF` cách xa cả `EC` lẫn `EV`. Điều này hàm ý rằng cả `n` lẫn `p` đều nhỏ, tức là các nồng độ hạt tải di động nhỏ hơn nhiều so với `ND`. Trong vùng này, `QD` được cho bởi Phương trình `6.3`.

**Hình 6.10c** trình bày tình huống trong đảo chiều. Ở đây, điện áp cổng `DC` âm đủ lớn để các vùng tại bề mặt bị cong đủ xa để đặt `EF` gần `EV`. Điều này có nghĩa là quần thể lỗ trống đáng kể tại bề mặt, tức là đảo chiều đã xảy ra và bề mặt là loại `P`. Bây giờ chúng ta có thể hiểu tại sao `QG` bổ sung được cân bằng bởi `QI` thay vì `QD` trong đảo chiều. Sự tăng thêm điện áp âm trên cổng sẽ cố gắng cong các vùng hơn nữa trong chất bán dẫn và di chuyển `EF` gần `EV` hơn. Tuy nhiên, chúng ta đã thấy trong Chương `1` rằng việc di chuyển `EF` gần `EV` hơn sẽ dẫn đến sự tăng theo hàm mũ của `p`. (Xem các Phương trình `1.10` hoặc `1.14` chẳng hạn.) Vì điều này, chỉ cần một sự di chuyển rất nhỏ của `EF` so với `EV` là cần thiết để cung cấp đủ `QI` để cân bằng `QG` bổ sung. Tham chiếu lại Phương trình `6.5`, chúng ta thấy rằng việc tăng `QG` sau khi đảo chiều đạt được sẽ dẫn đến sự tăng rất nhỏ trong `xD` và do đó trong `QD`, và hầu hết sự tăng `QG` sẽ được cân bằng bởi sự tăng trong `QI`. Do đó chúng ta nói `xD` bị "ghim" tại `xDMax` một khi đảo chiều xảy ra.

Có một vài khái niệm cơ bản khác mà chúng ta cần hiểu về các phép đo `CV` trước khi thảo luận về cách chúng có thể được sử dụng để đánh giá các chất cách điện và mặt tiếp xúc chất cách điện/bán dẫn. Các đường cong `CV` mà chúng ta đã mô tả đến điểm này được gọi là các đường cong `CV` tần số cao (`HF`). Điều này đơn giản có nghĩa là tín hiệu `AC` nhỏ được sử dụng để đo điện dung `MOS` là tín hiệu tần số vừa phải cao (thường `100 kHz` đến `1 MHz`). Chúng ta cần xem xét tại sao tần số này lại quan trọng.

Xét lại điều kiện đảo chiều trong **Hình 6.9c** hoặc **Hình 6.10c**. Giả sử chúng ta đã áp điện áp cổng `DC` `-VG` đủ lâu để hệ đạt đến cân bằng. (Chúng ta sẽ định nghĩa điều này kéo dài bao lâu trong thời gian ngắn.) Ở trạng thái cân bằng, lớp đảo chiều hiện diện và `xD` bị "ghim" tại `xDMax`. Giả sử bây giờ chúng ta áp một tín hiệu `HF` nhỏ để đo điện dung cấu trúc. Tín hiệu `AC` được chồng lên `-VG` và do đó điều biến `QG` rất nhỏ. Sự thay đổi trong `QG` này phải được cân bằng bởi một sự thay đổi trong `QD` hoặc `QI`. Ở trạng thái cân bằng, `QI` sẽ thay đổi như chúng ta đã thấy ở trên. Tuy nhiên, tần số cao trong ngữ cảnh này có nghĩa là `QG` đang được điều biến nhanh hơn so với tốc độ `QI` có thể phản ứng. Nếu điều này đúng, thì lựa chọn duy nhất hệ có là điều biến `QD` để cung cấp điện tích cân bằng. Nếu điều này xảy ra, thì việc cân bằng điện tích xảy ra giữa cổng và đáy của vùng suy giảm. Cạnh đáy của vùng suy giảm di chuyển lên xuống cùng với điện áp cổng, cung cấp `∆QD` cần thiết để cân bằng `∆QG`. Do đó, điện dung đo được là giữa hai bản cực đó (`Cox` nối tiếp với `CD`). Đối với bất kỳ `-VG` nào trong vùng đảo chiều, `xD` ở `xDMax` và do đó `CD` ở `CDMin`. Đây là lý do tại sao phép đo điện dung `HF` tạo ra điện dung cực tiểu đối với `VG` âm độc lập với `VG`.

Vậy tại sao `QI` không thể thay đổi nhanh như tín hiệu tần số cao trên cổng? Câu trả lời đơn giản là không có nguồn lỗ trống bổ sung sẵn có trong đế để cung cấp `∆QI`. Có rất ít lỗ trống hiện diện trong một chất bán dẫn loại `N`. Các cơ chế thường sẵn có duy nhất để tạo hoặc loại bỏ lỗ trống là phát sinh và tái hợp nhiệt tương ứng, và các quá trình này khá chậm trong các vật liệu như silicon có thời gian sống hạt tải dài. Kết quả là `QI` không thể thay đổi nhanh chóng và đường cong `CV HF` đo được một giá trị cực tiểu không đổi trong đảo chiều.

Bây giờ giả sử chúng ta làm chậm tín hiệu `AC` trên cổng. Nếu chúng ta giảm tần số xuống một giá trị đủ thấp (thường dưới `1 Hz` đối với silicon), thì các quá trình phát sinh và tái hợp có thể theo kịp tín hiệu `AC` và `QI` có thể đi theo các thay đổi trong `QG`. Bây giờ chúng ta đo gì cho đường cong `CV`? Câu trả lời, không ngạc nhiên, là bây giờ chúng ta đo đường cong `CV` tần số thấp (`LF`). Nếu `QI` đi theo `QG`, thì điện dung đo được trong cấu trúc sẽ chỉ là điện dung oxide vì các bản cực trên và dưới của tụ điện nơi `Q` đang thay đổi nằm ở hai cạnh của oxide. Do đó chúng ta nên kỳ vọng rằng đường cong `CV` sẽ trở lên đến `Cox` trong vùng đảo chiều. Đây thực ra là điều xảy ra và đường cong thu được là đường cong `CV LF`. **Hình 6.11** minh họa các đường cong `HF` và `LF`. Lưu ý rằng điểm mà các đường cong `CV HF` hoặc `LF` lý tưởng này đạt cực tiểu tương ứng với sự bắt đầu của đảo chiều và do đó là điện áp ngưỡng cho cấu trúc `MOS`.

**Hình 6.11** cũng minh họa điều kiện suy giảm sâu (`deep depletion`) có thể quan sát được trong các tụ điện `MOS`. Chúng ta đã thảo luận trường hợp này định tính trong Chương `4` (Mục `4.4.3`) trong mối liên hệ với việc đo thời gian sống phát sinh hạt tải trong chất bán dẫn. Suy giảm sâu xảy ra nếu điện áp phân cực `DC` trên tụ điện được quét quá nhanh vào vùng đảo chiều. Nếu điều này được thực hiện, các lỗ trống cần thiết cho lớp đảo chiều không thể được tạo ra đủ nhanh để đi theo điện áp "DC" được áp. Nếu `QI` không thể thay đổi đủ nhanh, các thay đổi trong `QG` chỉ có thể được cân bằng bởi `QD`. Do đó một vùng suy giảm sâu hơn giá trị cân bằng hình thành. Một điện dung nhỏ hơn giá trị cân bằng được đo, dần dần hồi phục về `CDMin` khi sự phát sinh lỗ trống diễn ra.

---

**Hình 6.11:** Các đường cong `CV MOS` lý tưởng ở tần số cao và thấp. Cũng được trình bày là đường cong `CV` suy giảm sâu.

---

Phương trình `1.20` đã cho tốc độ tái hợp hoặc phát sinh thực từ mô hình `Shockley-Read-Hall`. Trong một vùng suy giảm, `n` và `p` là không đáng kể và `U` rút gọn thành

---

> **[Công thức toán]**
>
> $$
> U = -\frac{n_i}{2\tau_0}
> \tag{6.6}
> $$

---

Giả sử rằng tốc độ phát sinh này duy trì xuyên suốt thể tích của vùng suy giảm, thì mật độ dòng điện tương ứng với `U` đơn giản là

---

> **[Công thức toán]**
>
> $$
> J = \frac{qn_i x_D}{2\tau_0}
> \tag{6.7}
> $$

---

Dòng điện này sẽ chảy đến bề mặt, cung cấp các lỗ trống cho lớp đảo chiều. Để tránh suy giảm sâu, tốc độ mà điện áp "DC" được quét trên tụ điện `MOS` phải nhỏ hơn

---

> **[Công thức toán]**
>
> $$
> \frac{dV_G}{dt} < \frac{J}{C_{ox}} = \frac{qn_i x_{DMax}}{2\tau_0 C_{ox}}
> \tag{6.8}
> $$

---

Trong thực tế, điều này có nghĩa là tốc độ quét "DC" dưới khoảng `0,1 V s⁻¹` phải được sử dụng.

---
## Ví Dụ:

Trong một cấu trúc thực nghiệm (trình bày dưới đây), một vùng `N+` phosphorus được hình thành bằng cấy ion sử dụng một `mask` `SiO₂` dày `50 nm`. Một điện cực kim loại sau đó được hình thành như trình bày và phép đo `C-V` được thực hiện ở vùng bên ngoài vùng `N+`. Phép đo cho `C = Cox` đối với tất cả các giá trị điện áp được áp như trình bày. Giải thích điều gì có thể đã xảy ra sai trong thí nghiệm này. Tức là giải thích tại sao không quan sát thấy sự đảo chiều bề mặt trong phép đo `C-V`.

---

**Hình 6.12:** Cấu trúc tụ điện `MOS` với phép đo `CV` "bất thường".

---

### Lời Giải:

Mặc dù có thể có một số giải thích, quan sát cơ bản ở đây là điện áp cổng dường như không có tác động đáng kể đến silicon bên dưới. Điều này có thể xảy ra nếu có các điện tích tại hoặc rất gần mặt tiếp xúc `Si/SiO₂` kết thúc các đường sức trước khi chúng xuyên vào silicon. Điều này có thể được gây ra bởi một mặt tiếp xúc `Si/SiO₂` rất kém, nhưng không có gì trong `process flow` gợi ý rằng điều này đã xảy ra (trừ khi có tổn thương từ quá trình cấy không được ủ đúng cách). Một giải thích có khả năng hơn là oxide `0,05 µm` không đủ dày để che chắn quá trình cấy và kết quả là quá trình cấy `N+` đã xuyên vào khắp nơi. Nếu điều này xảy ra, sẽ có đủ nguyên tử donor sẵn có để kết thúc trường cổng rất gần bề mặt. Do đó, khi `+VG` được áp, vật liệu cố gắng bắt đầu suy giảm, nhưng vì mức pha tạp rất cao gần bề mặt, vùng suy giảm `xD` cực kỳ nông. Do đó điện dung gắn với `xD` rất lớn và tổng điện dung (`Cox` nối tiếp với `CD`) về cơ bản chỉ là `Cox`. Chúng ta sẽ thảo luận các vấn đề cấy và che chắn cẩn thận hơn trong Chương `8`.

---

Chúng ta đã thấy trong Mục `6.2` rằng một số điện tích nói chung gắn với các mặt tiếp xúc chất cách điện/bán dẫn. Các điện tích này gây ra các dịch chuyển và méo trong các đường cong `CV` vì chúng đòi hỏi điện tích cổng `QG` để cân bằng chúng. **Hình 6.13** minh họa các hiệu ứng này trên đường cong `CV HF` "lý tưởng". `Qf` là một điện tích dương cố định hiện diện trong oxide, gần mặt tiếp xúc `SiO₂/Si`. Một điện tích dương như vậy sẽ tạo ra một điện tích ảnh âm tương ứng trong silicon, thực chất làm cho bề mặt silicon loại `N` hơn và do đó khó đảo chiều sang loại `P` hơn. Điều này biểu hiện như một sự dịch chuyển ngang trong đường cong `CV`, với độ lớn của sự dịch chuyển đơn giản được cho bởi `qQf/Cox`. Do đó, phép đo sự dịch chuyển này cho phép tính toán độ lớn của `Qf`. Một sự dịch chuyển ngang bổ sung xảy ra nói chung vì sự khác biệt về công thoát (`work function`) của kim loại và chất bán dẫn `φMS`. Công thoát theo định nghĩa là năng lượng cần thiết để loại bỏ một electron trong vật liệu ở năng lượng `EF` đến một vị trí ngay bên ngoài vật liệu. Đây là một tính chất có thể đo được của một vật liệu và nói chung được biết đối với bất kỳ thí nghiệm cụ thể nào. Do đó độ lệch ngang trong đường cong `CV` do `φMS` được biết. Hai số hạng này, `φMS` và `qQf/Cox` cùng nhau (`φMS - qQf/Cox`) chiếm sự tăng trong điện áp cổng cần thiết để gây đảo chiều và thường được gộp lại và gọi là điện áp dải phẳng (`flat band voltage`) `VFB` vì nếu một điện áp cổng có độ lớn này được áp, các vùng trong chất bán dẫn sẽ phẳng. Các số hạng này cũng xuất hiện trong điện áp bật của một transistor `MOS` (xem Phương trình `4.1`).

Nếu các điện tích di động (`Qm`) hoặc điện tích bẫy oxide (`Qot`) hiện diện, chúng tạo ra hiệu ứng tương tự như `Qf`. Tức là, chúng gây ra một sự dịch chuyển ngang trong đường cong `CV`. Sự khác biệt thực sự duy nhất là các điện tích này thường không nằm trực tiếp tại mặt tiếp xúc `SiO₂/Si`, và do đó độ lớn của sự dịch chuyển mà chúng gây ra bị giảm theo tỷ lệ với khoảng cách của chúng so với mặt tiếp xúc. (Một điện tích dương nằm ở phần trung tâm của oxide sẽ tạo ra một điện tích ảnh cân bằng, một phần trên cổng và một phần trong silicon.)

Đường cong `CV` "méo" được trình bày trong **Hình 6.13** minh họa điều xảy ra khi các bẫy mặt tiếp xúc `Qit` hiện diện. Chúng ta đã thấy trong Mục `6.2` rằng các bẫy này có thể có các mức năng lượng xuyên suốt vùng cấm. Khi điện áp cổng được áp khiến bề mặt chất bán dẫn di chuyển từ tích lũy sang suy giảm sang đảo chiều, quét ra một đường cong `CV`, `EF` tại bề mặt chất bán dẫn sẽ di chuyển từ cạnh vùng này đến cạnh vùng kia (`EC` sang `EV` trong ví dụ loại `N` mà chúng ta đã xem xét). Kết quả là, các bẫy `Qit` sẽ lấp đầy và làm trống khi `EF` di chuyển qua các mức năng lượng của chúng. Khi điều này xảy ra, đường cong `CV` sẽ méo khỏi hình dạng lý tưởng của nó. Dạng của sự méo phụ thuộc vào mật độ và các mức năng lượng của các bẫy `Qit`. Trong **Hình 6.13**, vùng được ghi nhãn `A` tương ứng với các trạng thái mặt tiếp xúc gần `EC`, `B` tương ứng với các trạng thái gần giữa vùng cấm, và `C` tương ứng với các trạng thái gần `EV`. Giả thiết thường được thực hiện là các trạng thái mặt tiếp xúc không thể đi theo tín hiệu `HF` được sử dụng để đo điện dung. Tức là, chúng không nạp và xả khi tín hiệu `HF` thay đổi. Nhưng các bẫy này sẽ phản ứng với tín hiệu `DC` được áp trên cổng vì chúng ta giả sử rằng tín hiệu này được áp đủ lâu để đạt cân bằng. Do đó `QG` được cân bằng một phần bởi `Qit`. Kết quả là sự kéo dãn của đường cong `CV` dọc theo trục ngang (điện áp `DC`).

---

**Hình 6.13:** Các đường cong `CV MOS HF` minh họa một số sự không lý tưởng có thể hiện diện trong các cấu trúc thực nghiệm thực tế. `A`, `B` và `C` minh họa các hiệu ứng của các trạng thái mặt tiếp xúc với các mức năng lượng khác nhau trong vùng cấm silicon.

---

Một số phương pháp đã được phát triển để trích xuất thực nghiệm mật độ trạng thái mặt tiếp xúc từ các phép đo `CV` trên các tụ điện `MOS`. Nhiều phương pháp trong số này được mô tả chi tiết trong các tài liệu tham khảo như `[6.9, 6.10]`. Phương pháp được sử dụng phổ biến nhất là phương pháp "tựa tĩnh" (`quasi-static`) hay `LF` được minh họa trong **Hình 6.14**. Trong phương pháp này, các đường cong `CV HF` và `LF` được chồng lên từ các phép đo trên cùng một tụ điện `MOS`. Giả thiết rằng các trạng thái mặt tiếp xúc không thể phản ứng với phép đo `HF` và chúng phản ứng với phép đo tần số thấp. Trong thực tế, điều này có nghĩa là `HF` phải đủ cao để các bẫy không thể nạp và xả ở tần số đo, và `LF` phải đủ thấp để cho phép các bẫy nạp và xả khi tín hiệu `LF` thay đổi. Nếu điều này là trường hợp, thì các bẫy sẽ hoạt động như một điện dung bổ sung đối với phép đo tần số thấp và `∆C` trong **Hình 6.14** sẽ tỷ lệ thuận với mật độ bẫy tại điện thế `DC` tương ứng với điểm đo. Thông tin này có thể được sử dụng để tạo ra một đồ thị như trình bày ở phần dưới của **Hình 6.14**. `Dit` là mật độ trạng thái mặt tiếp xúc tại một vị trí cụ thể trong vùng cấm. `Qit` có đơn vị `coulomb cm⁻²`, trong khi `Dit` có đơn vị `bẫy cm⁻² eV⁻¹`. Hình dạng `U` được trình bày định tính trong hình là điển hình của những gì nói chung được quan sát đối với mặt tiếp xúc `Si/SiO₂`.

---

**Hình 6.14:** Các đường cong `CV HF` và `LF` thực nghiệm điển hình được dùng để trích xuất mật độ trạng thái mặt tiếp xúc `Dit` theo hàm số năng lượng trong vùng cấm. Đồ thị `Dit` là điển hình của dữ liệu được trích xuất.

---

Một phép đo `CV` khác đôi khi hữu ích đặc trưng hóa `Qm`, mật độ điện tích di động trong chất cách điện. Thông thường các ion này là `Na⁺` hoặc `K⁺`, cả hai đều di động trong `SiO₂`, đặc biệt ở nhiệt độ hơi cao. Phương pháp đo được gọi là ứng suất nhiệt độ phân cực (`bias temperature stressing`) hay đơn giản là `BTS` và bao gồm việc thực hiện một phép đo `CV HF` ban đầu ở nhiệt độ phòng. Tụ điện `MOS` sau đó được nung đến `≈ 200°C` với một điện áp `DC` được áp trên cổng. Ở nhiệt độ này, `Na⁺` và `K⁺` rất di động và sẽ dễ dàng trôi lên trên hoặc xuống dưới trong `SiO₂`. Tụ điện sau đó được làm mát về nhiệt độ phòng (vẫn dưới điện áp phân cực), và một đường cong `CV HF` thứ hai được đo. Nếu sự trôi của `Qm` đã xảy ra, một sự dịch chuyển ngang trong đường cong `CV HF` sẽ được đo, giống như sự dịch chuyển ngang trong **Hình 6.13** do `Qf`. Mức độ dịch chuyển tỷ lệ thuận với `Qm`. Đôi khi một quy trình `BTS` thứ hai với điện áp phân cực ngược chiều được sử dụng để trôi `Qm` đến mặt tiếp xúc `SiO₂` kia để sự khác biệt ngang giữa hai đường cong `CV` tương ứng với tổng `Qm` hiện diện bất kể nó ban đầu nằm ở đâu trong chất cách điện.

Một phép đo đơn giản khác về các tính chất chất cách điện có thể thực hiện với tụ điện `MOS` là đặc tuyến `I-V` của chất cách điện. Đối với các oxide mỏng (`< 10 nm`), phép đo này có thể đo trực tiếp các dòng đường hầm được sử dụng trong một số loại linh kiện bộ nhớ. Đối với các oxide dày hơn, các dòng điện này quá nhỏ để dễ dàng đo, nhưng một phép đo phá hủy về độ bền đánh thủng điện môi của oxide đôi khi được thực hiện đơn giản bằng cách tăng dần điện áp qua oxide cho đến khi đánh thủng xảy ra. (Xem **Hình 4.15**.) Đối với các lớp `SiO₂` chất lượng cao, điều này thường xảy ra ở khoảng `10 - 15 MV cm⁻¹`. Nếu một số lượng lớn các tụ điện được đo trên một wafer, một đồ thị histogram của các điện trường đánh thủng đo được có thể cung cấp thông tin về mật độ khuyết tật trong các oxide.

Chúng ta đã đề cập ngắn gọn trước đó `QBD` hay điện tích đến đánh thủng có thể đi qua một lớp `SiO₂` mỏng trước khi đánh thủng xảy ra. Quá trình suy giảm oxide khi điện tích đi qua nó là sự bẫy điện tích tại các vị trí khuyết tật trong oxide. Quá trình này cũng có thể được theo dõi sử dụng tụ điện `MOS`. Nếu một dòng điện `DC` được ép qua tụ điện `MOS` trong một khoảng thời gian và các phép đo `CV` được thực hiện trước và sau quá trình này, thì điện tích bị bẫy sẽ biểu hiện như `Qot`. Do đó, các đường cong `CV` trước và sau sẽ cho thấy một sự dịch chuyển ngang có độ lớn tỷ lệ thuận với `Qot` như minh họa trong **Hình 6.13**. Một chuỗi các thí nghiệm như vậy tạo ra một đồ thị `Qot` theo thời gian dòng điện được ép qua oxide. Việc ép dòng điện qua chất cách điện cũng có thể tạo ra tổn thương tại mặt tiếp xúc `Si/SiO₂`. Nếu điều này xảy ra, tổn thương như vậy cũng hiển thị trong các đường cong `CV` thông qua sự méo của đường cong mà `Qit` tạo ra (cũng được trình bày trong **Hình 6.13**).

Cuối cùng, trong hầu hết các cấu trúc `MOS` hiện đại, mức pha tạp không phải là hằng số theo chiều sâu như chúng ta đã giả sử trong thảo luận đến điểm này. Thực ra điều này cung cấp một cơ hội mạnh mẽ khác cho các phép đo `CV`. Vì độ sâu suy giảm `xD` phụ thuộc vào mức pha tạp, một phép đo `C-V` cũng có thể được sử dụng để trích xuất `ND` hoặc `NA` theo chiều sâu. Đây là khả năng phân tích biên dạng pha tạp mạnh mẽ, mà chúng ta sẽ thảo luận trong Chương `7`.

Do đó, tụ điện `MOS` có thể cung cấp một lượng rất lớn thông tin về các chất cách điện và mặt tiếp xúc `Si/SiO₂`. Cấu trúc đơn giản này đã có tác động sâu sắc đến ngành công nghiệp bán dẫn đến mức cả cuốn sách đã được viết về nó `[6.10]`.

Tóm lại, chúng ta thấy rằng có nhiều kỹ thuật đo đa dạng sẵn có để xác định các tính chất chất cách điện. Chiều dày của một lớp cách điện lắng đọng hay được mọc có thể thu được qua các phép đo vật lý, quang học hoặc điện. Các tính chất mặt tiếp xúc giữa chất cách điện và chất bán dẫn bên dưới có thể đo trực tiếp qua các phương pháp `CV`. Và mật độ khuyết tật có thể thu được qua các phép đo đánh thủng phá hủy trên số lượng lớn tụ điện. Tất cả các kỹ thuật này đã được áp dụng rộng rãi cho cả mặt tiếp xúc oxide mọc nhiệt/`Si` lẫn các cấu trúc chất cách điện/bán dẫn tổng quát hơn. Chúng ta sẽ tìm thấy nhiều ví dụ về các phép đo như vậy xuyên suốt văn bản này. Một điểm cuối cùng, mặc dù có thể hiển nhiên, là mặc dù tất cả các ví dụ chúng ta đã trình bày trong phần này là đối với các đế loại `N`. Các đế loại `P` tạo ra các đồ thị `CV` tương tự ngoại trừ trục ngang bị đảo ngược (ảnh gương).

---

## 6.5 Các mô hình và mô phỏng

Một lượng đáng kể nỗ lực trong hơn `25` năm đã được dành để hiểu và mô hình hóa động học oxy hóa silicon. Chúng ta sẽ tập trung trong phần này vào một hệ thống phân cấp các mô hình đã được phát triển để giải thích và dự đoán động học oxy hóa và các tính chất của mặt tiếp xúc `Si/SiO₂`. Các mô hình tổng quát đầu tiên có từ công trình của Deal và Grove vào đầu những năm `1960` `[6.6]`. Công trình này dẫn đến mô hình tuyến tính-parabol vẫn còn được sử dụng ngày nay để mô hình hóa sự oxy hóa phẳng của silicon. Mô hình này không thể giải thích đầy đủ sự oxy hóa của các bề mặt có hình dạng, thường gặp trong các linh kiện `VLSI` hiện đại, và cũng không thể giải thích đầy đủ động học oxy hóa trong các môi trường hỗn hợp hoặc đối với các oxide rất mỏng. Cuối cùng, nó không thể giải thích tại sao sự oxy hóa ảnh hưởng đến các hiện tượng quy trình khác như khuếch tán chất pha tạp, thường ở khoảng cách xa từ bề mặt đang oxy hóa. Tuy nhiên, nó cung cấp một điểm khởi đầu hữu ích cho thảo luận của chúng ta và phần lớn công trình gần đây hơn về mô hình hóa được xây dựng dựa trên công trình tiên phong của Deal và Grove.

Nhiều mô hình mà chúng ta sẽ mô tả trong chương này đã được triển khai trong các chương trình mô phỏng quy trình. Chúng ta sẽ minh họa việc sử dụng các công cụ mô phỏng này khi mô tả các mô hình. Bộ mô phỏng mà chúng ta sẽ sử dụng là chương trình `SUPREM IV` của Đại học Stanford đã được triển khai trong các phiên bản thương mại sẵn có như `TSUPREM IV` `[6.11]` và `ATHENA` `[6.12]`. Các chương trình này triển khai nhiều (nhưng không phải tất cả) mô hình mà chúng ta sẽ thảo luận. `SUPREM IV` là một bộ mô phỏng `2D`, thường sẵn có và được sử dụng khá rộng rãi trong ngành công nghiệp bán dẫn. Các ví dụ mô phỏng trong chương này được chạy trên các phiên bản thương mại sẵn có của chương trình này.

Điều quan trọng cần lưu ý là nhiều mô hình oxy hóa mà chúng ta sẽ mô tả được phát triển đặc biệt để giải quyết một khía cạnh của vấn đề — ví dụ như sự oxy hóa của các đế pha tạp nặng. Việc chế tạo các cấu trúc linh kiện thực liên quan đến nhiều quá trình hoạt động đồng thời. Cách thực sự duy nhất để mô hình hóa các công nghệ như vậy là sử dụng một chương trình máy tính tích hợp tất cả các mô hình riêng lẻ và cho phép chúng hoạt động đồng thời trong một bước nhiệt độ cao. Đây là sức mạnh thực sự của các chương trình mô phỏng. Tuy nhiên, chính thực tế là các chương trình như vậy tích hợp các mô hình riêng lẻ, thậm chí có thể là các mô hình được phát triển độc lập với nhau, có nghĩa là các tương tác giữa các mô hình có thể chưa được kiểm tra đầy đủ thực nghiệm. Trên thực tế, các bộ mô phỏng thực sự trở thành phương tiện để kiểm tra tính tổng quát của các mô hình riêng lẻ. Ở cuối chương, chúng ta sẽ trình bày một số ví dụ về mô phỏng quy trình oxy hóa đầy đủ hơn — các ví dụ tích hợp nhiều mô hình đồng thời.

### 6.5.1 Động học mọc phẳng bậc nhất — Mô hình tuyến tính-parabol

Các ý tưởng trung tâm đằng sau mô hình Deal-Grove hay mô hình tuyến tính-parabol được minh họa trong **Hình 6.15**. (Lưu ý sự tương đồng của mô hình này với mô hình hiện hình `photoresist` mà chúng ta đã thảo luận trong mối liên hệ với **Hình 5.48**.) Chúng ta giả sử rằng một oxide có chiều dày nào đó `xi` đã hiện diện trên bề mặt silicon. Chúng ta cũng giả sử rằng cấu trúc là một chiều để mô hình này chỉ áp dụng cho các màng oxide mọc trên các đế phẳng. Oxide mọc bằng sự khuếch tán vào trong của chất oxy hóa đến mặt tiếp xúc oxide/silicon, nơi một phản ứng hóa học đơn giản như

---

> **[Biểu thức hóa học]**
>
> $$
> \text{Si} + \text{O}_2 \rightarrow \text{SiO}_2
> \tag{6.9}
> $$
>
> hoặc
>
> $$
> \text{Si} + 2\text{H}_2\text{O} \rightarrow \text{SiO}_2 + 2\text{H}_2
> \tag{6.10}
> $$

---

diễn ra. Ban đầu chúng ta giả sử rằng ba bước tuần tự là cần thiết để điều này xảy ra, mặc dù sau đó sẽ thấy chỉ có hai trong số chúng là quan trọng. **Hình 6.15** minh họa ba thông lượng gắn với quá trình. Thông lượng đầu tiên đại diện cho sự vận chuyển chất oxy hóa trong pha khí đến bề mặt oxide. Chúng ta có thể mô tả thông lượng này là

---

> **[Công thức toán]**
>
> $$
> F_1 = h_G(C_G - C_S)
> \tag{6.11}
> $$

---

trong đó `F₁` là thông lượng tính theo phân tử `cm⁻² s⁻¹`, `(CG - CS)` là sự chênh lệch nồng độ giữa dòng khí chính và bề mặt oxide, và `hG` là hệ số truyền khối (`mass transfer coefficient`) tính bằng `cm s⁻¹`. Quá trình được đại diện bởi `F₁` là sự khuếch tán pha khí của chất oxy hóa qua lớp biên hay lớp trì trệ (`stagnant layer`) luôn hình thành cạnh một vật thể rắn đặt trong khí đang chảy qua bề mặt của nó. Trong trường hợp oxy hóa, quá trình khuếch tán này rất nhanh so với các bước khác phải xảy ra và do đó `F₁` sẽ không quan trọng trong việc xác định động học mọc tổng thể. Các kỹ thuật xử lý khác như epitaxy và `CVD` cũng liên quan đến sự vận chuyển chất phản ứng từ pha khí đến bề mặt wafer, có thể bị giới hạn bởi quá trình vận chuyển này. Chúng ta sẽ thảo luận các tình huống này trong Chương `9`.

---

**Hình 6.15:** Thông lượng chất oxy hóa từ pha khí đến bề mặt silicon trong quá trình oxy hóa nhiệt. Đường đậm đại diện cho nồng độ `O₂` hoặc `H₂O`.

---

Chúng ta có thể liên hệ nồng độ chất oxy hóa ngay bên trong bề mặt oxide `CO`, với áp suất trong pha khí kề cạnh bề mặt, thông qua Định luật Henry.

---

> **[Công thức toán]**
>
> $$
> C_O = HP_S
> \tag{6.12}
> $$

---

Định luật này phát biểu rằng nồng độ cân bằng của một chất khí hòa tan trong chất rắn tỷ lệ thuận với áp suất riêng phần của chất đó tại bề mặt chất rắn. Nó đúng đối với các chất phân tử, vì vậy chúng ta giả sử rằng `O₂` hoặc `H₂O` được hấp thụ vào oxide. `PS` thường không phải là một tham số thực nghiệm đã biết, nên thuận tiện hơn khi viết nồng độ chất oxy hóa trong oxide theo `PG` là áp suất khí khối đã biết.

---

> **[Công thức toán]**
>
> $$
> C^* = HP_G
> \tag{6.13}
> $$

---

Chúng ta định nghĩa `C*` là nồng độ chất oxy hóa trong oxide sẽ ở cân bằng với `PG`. Vì sẽ thấy rằng `F₁` không phải là bước giới hạn tốc độ trong quá trình oxy hóa, điều này hàm ý rằng `C* ≈ CO` và `PG ≈ PS`. Do đó `C*` thực sự đại diện cho độ hòa tan của chất oxy hóa trong `SiO₂`. Từ định luật khí lý tưởng, chúng ta có

---

> **[Công thức toán]**
>
> $$
> C_G = \frac{P_G}{kT} \quad \text{và} \quad C_S = \frac{P_S}{kT}
> \tag{6.14}
> $$

---

Thay thế các Phương trình `6.12 - 6.14` vào `6.11` dẫn trực tiếp đến kết quả là

---

> **[Công thức toán]**
>
> $$
> F_1 = h(C^* - C_O)
> \tag{6.15}
> $$

---

trong đó `h = hG/HkT`. Thực nghiệm, chúng ta thấy rằng các thay đổi rộng về tốc độ dòng khí trong các lò oxy hóa, các thay đổi về khoảng cách giữa các wafer trên thuyền hay giá đỡ trong lò và các thay đổi về hướng wafer (đứng hay nằm trong lò) tạo ra ít sự khác biệt trong tốc độ oxy hóa. Các kết quả này hàm ý rằng `h` rất lớn, hay rằng chỉ cần một sự chênh lệch nhỏ giữa `C*` và `CO` là cần thiết để cung cấp thông lượng chất oxy hóa cần thiết.

Thông lượng `F₂` trong **Hình 6.15** đại diện cho sự khuếch tán của chất oxy hóa qua oxide đến mặt tiếp xúc `Si/SiO₂`. Sử dụng Định luật Fick, chúng ta có thể biểu diễn điều này là

---

> **[Công thức toán]**
>
> $$
> F_2 = -D\frac{\partial C}{\partial x} = D\frac{C_O - C_I}{x_O}
> \tag{6.16}
> $$

---

trong đó `D` là hệ số khuếch tán của chất oxy hóa trong oxide, `CO` và `CI` là các nồng độ tại hai mặt tiếp xúc, và `xO` là chiều dày oxide. Khi viết biểu thức này, chúng ta đã giả sử rằng quá trình ở trạng thái dừng (không thay đổi nhanh theo thời gian) và rằng không có sự mất mát chất oxy hóa khi nó khuếch tán qua oxide. Trong các điều kiện này, `F₂` phải là hằng số qua oxide và do đó đạo hàm có thể được thay thế đơn giản bằng một gradient không đổi. Nồng độ chất oxy hóa giảm tuyến tính qua oxide như trình bày trong **Hình 6.15**. Bằng chứng thực nghiệm dường như gợi ý rằng `O₂` khuếch tán ở dạng phân tử qua `SiO₂`, có khả năng theo hướng kẽ giữa các nguyên tử trong oxide. Mặt khác, `H₂O` dường như khuếch tán theo cách phức tạp hơn, tương tác với ma trận `SiO₂`. Hệ số khuếch tán hiệu dụng của cả `O₂` lẫn `H₂O` có cùng bậc độ lớn (khoảng `5 × 10³ µm² hr⁻¹` ở `1100°C`).

Phần thứ ba của quá trình oxy hóa là phản ứng tại mặt tiếp xúc `Si/SiO₂`. Chúng ta biểu diễn điều này bằng thông lượng thứ ba

---

> **[Công thức toán]**
>
> $$
> F_3 = k_S C_I
> \tag{6.17}
> $$

---

Tốc độ mà phản ứng này diễn ra phải tỷ lệ thuận với nồng độ chất oxy hóa tại mặt tiếp xúc `CI`. Cũng có nhiều yếu tố khác nhiều khả năng liên quan đến phản ứng như sự phá vỡ liên kết `Si-Si`, sự hình thành liên kết `Si-O` và có thể sự phân ly `O₂` hoặc `H₂O`. Tất cả các hiệu ứng này và các hiệu ứng khác được gộp vào `kS`, được gọi là hằng số tốc độ phản ứng mặt tiếp xúc (`interface reaction rate constant`, `cm s⁻¹`). Chúng ta sẽ quay lại thảo luận chi tiết hơn về phản ứng mặt tiếp xúc này ở phần sau trong chương này.

Trong các điều kiện trạng thái dừng, ba thông lượng đại diện cho quá trình oxy hóa phải bằng nhau vì chúng xảy ra nối tiếp nhau và quá trình tổng thể sẽ tiến hành với tốc độ của quá trình chậm nhất. Vậy `F₁ = F₂ = F₃`. Kết hợp các Phương trình `6.15 - 6.17` dẫn đến

---

> **[Công thức toán]**
>
> $$
> C_I = \frac{C^*}{1 + \dfrac{k_S}{h} + \dfrac{k_S x_O}{D}}
> \approx
> \frac{C^*}{1 + \dfrac{k_S x_O}{D}}
> \tag{6.18}
> $$
>
> $$
> C_O = \frac{C^*\!\left(1 + \dfrac{k_S x_O}{D}\right)}{1 + \dfrac{k_S}{h} + \dfrac{k_S x_O}{D}}
> \approx C^*
> \tag{6.19}
> $$

---

Khi viết các biểu thức vế phải trong các phương trình này, chúng ta đã sử dụng quan sát thực nghiệm rằng `h` rất lớn. Về mặt vật lý, chúng ta có thể xem quá trình tổng thể như liên quan đến hai phản ứng mặt tiếp xúc (`h` và `kS`) và một quá trình khuếch tán. Trong hai phản ứng mặt tiếp xúc, quá trình tại bề mặt oxide (hấp thụ khí) diễn ra rất nhanh so với hóa học xảy ra tại `Si/SiO₂` và do đó `h` không đáng kể so với `kS`.

Có hai trường hợp giới hạn quan tâm trong các Phương trình `6.18` và `6.19`. Chúng được minh họa trong **Hình 6.16**. Các trường hợp này xảy ra khi `kSxO/D` nhỏ hơn nhiều so với `1` hoặc lớn hơn nhiều so với `1`. Phía bên trái của **Hình 6.16** minh họa trường hợp khi `kSxO/D << 1`. Trong trường hợp này, `CI ≈ C*` và biên dạng chất oxy hóa về cơ bản là phẳng qua oxide. Về mặt vật lý, điều này có nghĩa là quá trình khuếch tán không giới hạn tốc độ, hay nói cách khác, chất oxy hóa đang được cung cấp đến mặt tiếp xúc `Si/SiO₂` với tốc độ nhanh so với tốc độ cần thiết để duy trì phản ứng hóa học đang xảy ra ở đó. Điều kiện này thường được gọi là kiểm soát bởi tốc độ phản ứng (`reaction rate controlled`) vì mặt tiếp xúc đang xác định tốc độ oxide mọc. Nói chung, đây là trường hợp đối với các oxide mỏng vì `kSxO/D << 1` khi `xO` nhỏ. Chiều dày oxide tại đó `kSxO/D ≈ 1` thay đổi theo nhiệt độ vì `kS` và `D` thay đổi theo nhiệt độ, nhưng thường trong khoảng `50 - 200 nm`.

---

**Hình 6.16:** Các trường hợp giới hạn trong oxy hóa silicon. Phản ứng mặt tiếp xúc là bước giới hạn tốc độ ở bên trái; sự vận chuyển chất oxy hóa qua `SiO₂` giới hạn tốc độ ở bên phải.

---

Đối với các chiều dày oxide lớn hơn giá trị này, sự mọc ngày càng tiến gần hơn đến trường hợp giới hạn được trình bày ở bên phải của **Hình 6.16**. Trong trường hợp này, `kSxO/D >> 1` và biên dạng chất oxy hóa trong oxide trở nên tuyến tính, với `CI ≈ 0`. Trong trường hợp này, chất oxy hóa đang phản ứng tại mặt tiếp xúc nhanh như khi nó đến và tốc độ mọc tổng thể bị giới hạn bởi quá trình khuếch tán. Điều này thường được gọi là chế độ kiểm soát bởi khuếch tán (`diffusion controlled regime`).

Kết hợp các Phương trình `6.17` và `6.18`, chúng ta có

---

> **[Công thức toán]**
>
> $$
> \frac{dx}{dt} = \frac{F}{N_1} = \frac{k_S C^*}{N_1\!\left[1 + \dfrac{k_S}{h} + \dfrac{k_S x_O}{D}\right]}
> \tag{6.20}
> $$

---

trong đó `N₁` là số phân tử chất oxy hóa được kết hợp trên một đơn vị thể tích oxide mọc. `N₁ = 2,2 × 10²² cm⁻³` đối với oxy hóa bằng `O₂` và gấp đôi giá trị này đối với oxy hóa bằng `H₂O`. Tích phân phương trình này từ chiều dày oxide ban đầu `xi` đến chiều dày cuối `xO` dẫn chúng ta đến kết quả cuối cùng mô tả động học mọc oxide.

---

> **[Công thức toán]**
>
> $$
> x_O^2 - x_i^2 + A(x_O - x_i) = Bt
> \tag{6.21}
> $$
>
> hay viết lại:
>
> $$
> \frac{x_O^2 - x_i^2}{B} + \frac{x_O - x_i}{B/A} = t
> \tag{6.22}
> $$
>
> trong đó:
>
> $$
> B = \frac{2DC^*}{N_1}
> \tag{6.23}
> $$
>
> $$
> \frac{B}{A} = \frac{C^*}{N_1\!\left(\dfrac{1}{k_S} + \dfrac{1}{h}\right)} \approx \frac{C^* k_S}{N_1}
> \tag{6.24}
> $$

---

`B` và `B/A` thường được gọi là hằng số tốc độ parabol và hằng số tốc độ tuyến tính tương ứng, vì các số hạng `x²` và `x` mà chúng xuất hiện trong đó. Về mặt vật lý, chúng đại diện cho đóng góp của thông lượng `F₂` (khuếch tán chất oxy hóa) và `F₃` (phản ứng mặt tiếp xúc) tương ứng.

Đôi khi thuận tiện khi viết lại quy luật mọc tuyến tính-parabol theo dạng sau.

---

> **[Công thức toán]**
>
> $$
> \frac{x_O^2}{B} + \frac{x_O}{B/A} = t + \tau
> \tag{6.25}
> $$
>
> trong đó:
>
> $$
> \tau = \frac{x_i^2 + Ax_i}{B}
> \tag{6.26}
> $$

---

Trong các biểu thức này, `xi` hoặc `τ` tính đến bất kỳ oxide nào hiện diện ở đầu quá trình oxy hóa. Chúng cũng có thể được dùng để phù hợp tốt hơn với dữ liệu trong chế độ oxide mỏng "bất thường" trong `O₂` khô như chúng ta sẽ thấy sau này. Giải phương trình parabol dẫn đến biểu thức tường minh sau đây cho chiều dày oxide theo thời gian mọc.

---

> **[Công thức toán]**
>
> $$
> x_O = \frac{A}{2}\left\{\sqrt{1 + \frac{t + \tau}{A^2/4B}} - 1\right\}
> \tag{6.27}
> $$

---

Có hai dạng giới hạn của quy luật mọc tuyến tính-parabol có thể thấy trực tiếp từ Phương trình `6.25`. Chúng xảy ra khi một trong hai số hạng chiếm ưu thế, dẫn đến

---

> **[Công thức toán]**
>
> $$
> x_O \approx \frac{B}{A}(t + \tau) \quad \text{(tuyến tính)}
> \qquad \text{hoặc} \qquad
> x_O^2 \approx B(t + \tau) \quad \text{(parabol)}
> \tag{6.28}
> $$

---

Lý do để gọi `B/A` và `B` là hằng số tốc độ tuyến tính và parabol trở nên rõ ràng khi quy luật mọc được biểu diễn theo các dạng này. Số hạng tuyến tính sẽ chiếm ưu thế đối với các giá trị `x` nhỏ; số hạng parabol đối với các giá trị `x` lớn hơn. Do đó, sự mọc `SiO₂` trên một wafer silicon trần thường bắt đầu với đặc trưng tuyến tính `x` theo `t`, trở nên parabol khi oxide dày lên.

Các Phương trình `6.23` và `6.24` gợi ý rằng chúng ta có thể tính toán các giá trị cho `B` và `B/A` và do đó kiểm tra các dự đoán của mô hình tuyến tính-parabol với thực nghiệm. Trên thực tế, `B` và `B/A` thường được xác định thực nghiệm bằng cách trích xuất chúng từ dữ liệu mọc. Lý do để áp dụng cách tiếp cận này đơn giản là chúng ta thường không biết tất cả các tham số trong các Phương trình `6.23` và `6.24`. Đặc biệt, `kS` chứa rất nhiều "vật lý ẩn" gắn với phản ứng mặt tiếp xúc. Tuy nhiên, điều chúng ta có thể làm là so sánh các giá trị thực nghiệm của `B` và `B/A` với dạng của các Phương trình `6.23` và `6.24` để kiểm tra tính hợp lý của mô hình tuyến tính-parabol.

**Hình 6.17** gợi ý cách các hằng số tốc độ oxy hóa có thể được trích xuất từ dữ liệu thực nghiệm. Bằng cách vẽ lại dữ liệu chiều dày oxide theo thời gian ở dạng trình bày ở bên phải trong hình, `B` được trích xuất trực tiếp từ độ dốc của đường thẳng và `A` và do đó `B/A` được trích xuất từ giao điểm. Cách tiếp cận này đã được sử dụng rộng rãi để xác định các giá trị cho `B` và `B/A` đối với một dải rộng các điều kiện thực nghiệm. Nếu dữ liệu thực nghiệm thực sự nằm trên một đường thẳng khi được vẽ theo dạng của **Hình 6.17**, thì dữ liệu được mô tả tốt bởi một quy luật mọc tuyến tính-parabol. Trên thực tế, có nhiều điều kiện mọc không dẫn đến dữ liệu là một đường thẳng, một số trong đó chúng ta sẽ thảo luận trong các phần sau của chương này. Trong các trường hợp này, chúng ta có thể kết luận rằng dữ liệu không được mô hình hóa tốt bởi mô hình tuyến tính-parabol đơn giản mà chúng ta đã mô tả đến đây.

---

**Hình 6.17:** Trích xuất các hằng số tốc độ từ dữ liệu thực nghiệm chiều dày oxide theo thời gian.

---

Khi các oxy hóa được thực hiện trên các bề mặt phẳng không có mẫu, trên các đế pha tạp nhẹ, trong các môi trường `O₂` hoặc `H₂O` đơn giản và khi chiều dày oxide lớn hơn khoảng `20 nm`, động học mọc thường được mô tả tốt bởi quy luật tuyến tính-parabol. Trong các điều kiện như vậy, các giá trị của `B` và `B/A` có thể được trích xuất dễ dàng. Thực nghiệm, chúng ta thấy rằng cả `B` lẫn `B/A` đều được mô tả tốt bởi các biểu thức Arrhenius có dạng

---

> **[Công thức toán]**
>
> $$
> B = C_1 \exp\!\left(-\frac{E_1}{kT}\right)
> \tag{6.29}
> $$
>
> $$
> \frac{B}{A} = C_2 \exp\!\left(-\frac{E_2}{kT}\right)
> \tag{6.30}
> $$

---

Trong các biểu thức này, `E₁` và `E₂` là các năng lượng hoạt hóa gắn với các quá trình vật lý mà `B` và `B/A` đại diện; `C₁` và `C₂` là các hằng số tiền mũ. Thường có ý nghĩa vật lý đáng kể có thể gắn với các năng lượng hoạt hóa được đo thực nghiệm khi các quan hệ Arrhenius được tuân theo. **Bảng 6.2** dưới đây liệt kê các giá trị thực nghiệm cho các tham số trong các Phương trình `6.29` và `6.30`. Các giá trị tương ứng cho `B` và `B/A` cũng được vẽ trong **Hình 6.18**. Trong **Bảng 6.2**, môi trường oxy hóa giữa ("wet O₂") tương ứng với một hệ oxy hóa trong đó `O₂` được bục qua `H₂O` ở `95°C`. Kết quả là một môi trường oxy hóa chủ yếu là `H₂O`, nhưng cũng chứa một ít `O₂`. Các loại hệ này phổ biến vài năm trước, mặc dù hầu hết các hệ oxy hóa `H₂O` ngày nay trực tiếp phản ứng `H₂` và `O₂` để tạo ra `H₂O` ở đầu sau của lò.

---

> **[Bảng thông số]**

| Môi trường | `B` | `B/A` |
|---|---|---|
| `O₂` khô | `C₁ = 7,72 × 10² µm² hr⁻¹`<br>`E₁ = 1,23 eV` | `C₂ = 6,23 × 10⁶ µm hr⁻¹`<br>`E₂ = 2,0 eV` |
| `O₂` ướt | `C₁ = 2,14 × 10² µm² hr⁻¹`<br>`E₁ = 0,71 eV` | `C₂ = 8,95 × 10⁷ µm hr⁻¹`<br>`E₂ = 2,05 eV` |
| `H₂O` | `C₁ = 3,86 × 10² µm² hr⁻¹`<br>`E₁ = 0,78 eV` | `C₂ = 1,63 × 10⁸ µm hr⁻¹`<br>`E₂ = 2,05 eV` |

**Bảng 6.2:** Các hằng số tốc độ mô tả động học oxy hóa silicon `(111)` ở tổng áp suất `1 atm`. Đối với các giá trị tương ứng đối với silicon `(100)`, tất cả các giá trị `C₂` phải được chia cho `1,68`.

---

Trước tiên xét hằng số tốc độ parabol `B`. Thực nghiệm, chúng ta thấy rằng năng lượng hoạt hóa `E₁` khá khác nhau đối với các môi trường `O₂` và `H₂O`. Phương trình `6.23` gợi ý rằng cơ chế vật lý chịu trách nhiệm cho `E₁` có thể là sự khuếch tán chất oxy hóa qua `SiO₂`. (`N₁` là hằng số và `C*` không được kỳ vọng tăng theo hàm mũ với nhiệt độ.) Thực ra, các phép đo độc lập về hệ số khuếch tán của `O₂` và `H₂O` trong `SiO₂` chỉ ra rằng các tham số này biến thiên theo nhiệt độ theo cùng cách như Phương trình `6.29` và với các giá trị `E₁` gần với những giá trị được trình bày trong **Bảng 6.2**. Hàm ý rõ ràng là `B` trong mô hình tuyến tính-parabol thực sự đại diện cho quá trình khuếch tán chất oxy hóa.

Các giá trị `E₂` cho `B/A` trong bảng đều khá gần `2 eV`. Phương trình `6.24` gợi ý rằng nguồn gốc vật lý của `E₂` nhiều khả năng gắn với hằng số tốc độ phản ứng mặt tiếp xúc `kS`. `kS` thực sự đại diện cho một số quá trình xảy ra tại mặt tiếp xúc `Si/SiO₂`. Chúng có thể bao gồm sự phân ly chất oxy hóa (`O₂ → 2O`), sự phá vỡ liên kết `Si-Si` và/hoặc sự hình thành liên kết `Si-O`. Theo truyền thống, năng lượng hoạt hóa `2 eV` đã được gắn với quá trình phá vỡ liên kết `Si-Si`, vì các phép đo của Pauling gợi ý rằng năng lượng liên kết `Si-Si` nằm trong khoảng phù hợp để giải thích các giá trị `B/A`. Tuy nhiên, phản ứng mặt tiếp xúc rất phức tạp và có khả năng các hiệu ứng khác cũng ảnh hưởng đến các giá trị `B/A` thực nghiệm. Một quan sát bổ sung ủng hộ ý tưởng rằng chính cái gì đó gắn với đế `Si` xác định `E₂` là `E₂` về cơ bản độc lập với môi trường oxy hóa. Nó cũng về cơ bản độc lập với hướng tinh thể của đế, gợi ý rằng `E₂` đại diện cho một phần cơ bản của quá trình oxy hóa, không phải cái gì đó chỉ gắn với đế.

---

**Hình 6.18:** `B` và `B/A` cho oxy hóa `O₂` và `H₂O` của silicon `<111>`. Các giá trị lấy từ các tham số trong **Bảng 6.2**.

---

Sử dụng các giá trị cho `B` và `B/A` trong **Bảng 6.2**, các **Hình 6.19** và **6.20** trình bày các đường cong chiều dày oxide theo thời gian được tính toán dự đoán bởi mô hình Deal-Grove. Ứng xử chung của tốc độ mọc tuyến tính ban đầu trở nên parabol khi oxide dày lên rõ ràng trong các đường cong tính toán này. Cũng rõ ràng từ các hình rằng `SiO₂` mọc nhanh hơn nhiều trong môi trường `H₂O` so với trong `O₂` khô. Lý do chính cho điều này là độ hòa tan của chất oxy hóa trong `SiO₂` (`C*` trong các Phương trình `6.23` và `6.24`) cao hơn nhiều đối với `H₂O` so với `O₂`. Ở `1100°C`, các giá trị điển hình cho `C*` là `≈ 5 × 10¹⁶ cm⁻³` đối với `O₂` khô và `≈ 3 × 10¹⁹ cm⁻³` đối với `H₂O`. Kết quả là, cả hai hằng số tốc độ, `B` và `B/A`, đều lớn hơn nhiều đối với `H₂O` so với `O₂`. Các oxy hóa bằng `O₂` khô do đó nói chung hữu ích để tạo ra các màng oxide đến `100 - 200 nm`. Các màng dày hơn giá trị này thường sẽ được mọc sử dụng các môi trường `H₂O`.

---

**Hình 6.19:** Các tốc độ oxy hóa được tính toán cho silicon `(100)` trong `O₂` khô dựa trên mô hình Deal-Grove. Các giá trị tham số lấy từ **Bảng 6.2**. Sự oxy hóa nhanh ban đầu cho khoảng `20 nm` đầu tiên không được đưa vào (`τ = 0`).

---

**Hình 6.20:** Các tốc độ oxy hóa được tính toán cho silicon `(100)` trong `H₂O` dựa trên mô hình Deal-Grove. Các giá trị tham số lấy từ **Bảng 6.2**.

---

## Ví Dụ:

Oxy hóa cục bộ (`local oxidation`) là một quy trình được sử dụng rộng rãi để cung cấp sự cách điện theo chiều ngang giữa các linh kiện trong các chip `IC`. Trong một số trường hợp, mong muốn thu được một bề mặt phẳng hơn so với `LOCOS` tiêu chuẩn cung cấp, và do đó một bước khắc silicon được sử dụng trước bước oxy hóa như minh họa trong **Hình 6.21**. Đối với cấu trúc được trình bày ở bên trái, với `0,5 µm` silicon được khắc trước khi oxy hóa, wafer phải được oxy hóa trong bao lâu ở `1000°C` trong `H₂O` để tạo ra oxide phẳng trình bày ở bên phải?

---

**Hình 6.21:** Quy trình `LOCOS` lõm (`recessed LOCOS`) trong đó silicon được khắc trước `LOCOS` để tạo ra bề mặt cuối cùng phẳng. "Mỏ chim" (`bird's beak`) được tạo ra tại các ranh giới của các cấu trúc như vậy không được minh họa ở đây (xem **Hình 6.40** ở phần sau trong chương).

---

### Lời Giải:

Có sự giãn nở thể tích `2,2X` trong quá trình oxy hóa nhiệt, vì vậy mọc `1 µm` `SiO₂` tiêu thụ `0,45 µm` silicon. Do đó, oxide đang mọc sẽ tiêu thụ thêm một chiều dày silicon (`y` bên dưới) khi lấp đầy rãnh khắc.

---

**Hình 6.22:** Hình học `LOCOS` lõm trình bày thêm silicon được tiêu thụ trong quá trình oxy hóa.

---

> **[Công thức toán - Kết quả tính toán]**
>
> $$
> \frac{y}{0.45} = y + 0.5 \implies y = 0.41\,\mu m
> $$
>
> Vì vậy, chúng ta cần mọc tổng chiều dày `SiO₂` là:
>
> $$
> x_O = 2.2\times(0.41 + 0.5)\times\frac{1}{2.2}\times 2.2
> $$
>
> Tổng `SiO₂` cần mọc: $x_O = 0.5 + 0.41\times 2.2 = 0.5 + 0.902 \approx 0.91\,\mu m$

---

Vậy chúng ta cần mọc tổng cộng `0,91 µm` `SiO₂`. Ở `1000°C` trong `H₂O`:

---

> **[Công thức toán - Kết quả tính toán]**
>
> $$
> B = 3.86\times10^2 \exp\!\left(-\frac{0.78\,\text{eV}}{kT}\right) = 0.316\,\mu\text{m}^2\,\text{hr}^{-1}
> $$
>
> $$
> \frac{B}{A} = \frac{1.63\times10^8}{1.68}\exp\!\left(-\frac{2.05\,\text{eV}}{kT}\right) = 0.75\,\mu\text{m}\,\text{hr}^{-1}
> $$
>
> $$
> \therefore\quad t = \frac{x^2}{B} + \frac{x}{B/A} = \frac{(0.91)^2}{0.316} + \frac{0.91}{0.75} = 3.83\,\text{giờ}
> $$

---

### 6.5.2 Các mô hình khác cho động học oxy hóa phẳng

Mô hình tuyến tính-parabol được mô tả ở trên là mô hình oxy hóa được chấp nhận rộng rãi nhất. Tuy nhiên, nó không giải thích được một số quan sát thực nghiệm, nhiều trong số đó chúng ta sẽ thảo luận trong các phần tiếp theo của chương này. Một thực tế đặc biệt quan trọng là các phép đo thực nghiệm về tốc độ mọc oxide trong `O₂` khô không được mô hình Deal-Grove dự đoán chính xác đối với các oxide mỏng dưới khoảng `20 nm`. Vì điều này và các vấn đề khác, nhiều mô hình khác đã được đề xuất, mỗi mô hình tuyên bố là sự cải tiến so với cách tiếp cận tuyến tính-parabol. Tuy nhiên, không có mô hình nào trong số này được chấp nhận rộng rãi. Chúng ta sẽ thảo luận ngắn gọn ở đây một vài mô hình thay thế này, để cung cấp một bức tranh rộng hơn về động học oxy hóa.

Năm `1987`, Reisman và cộng sự `[6.13]` đề xuất rằng một quy luật lũy thừa rất đơn giản có dạng

---

> **[Công thức toán]**
>
> $$
> x_O = a(t + t_i)^b \quad \text{hay} \quad x_O = a\!\left(t + \left(\frac{x_i}{a}\right)^{1/b}\right)^b
> \tag{6.31}
> $$

---

trong đó `a` và `b` là các hằng số đối với một tập điều kiện quy trình cụ thể và `ti` là thời gian tương ứng với sự mọc của bất kỳ oxide hiện có nào (`xi`) ở đầu quá trình — tương tự như `τ`, có thể phù hợp với tất cả dữ liệu oxy hóa `O₂` khô đã công bố. Khi khớp phương trình này với dữ liệu thực nghiệm, họ trích xuất các giá trị `b` giữa `0,25` và `1,0`, tùy thuộc vào nhiệt độ và áp suất riêng phần chất oxy hóa. Phương trình này có hai tham số khớp (`a` và `b`), giống như mô hình Deal-Grove có hai (`B` và `B/A`). Tuy nhiên, có những sự khác biệt then chốt giữa các mô hình. Thứ nhất, Reisman và cộng sự tuyên bố rằng Phương trình `6.31` có thể khớp với dữ liệu xuống đến chiều dày oxide về cơ bản bằng `0`. Không có chế độ mỏng bất thường như trong mô hình Deal-Grove. Thứ hai, cơ sở vật lý của các mô hình khá khác nhau. Mô hình Deal-Grove như chúng ta đã thấy dựa trên ý tưởng về khuếch tán chất oxy hóa và phản ứng mặt tiếp xúc, với mỗi quá trình chi phối sự mọc trong các điều kiện khác nhau. Trong một bài báo tiếp theo `[6.13]`, Nicollian và Reisman gợi ý rằng phản ứng mặt tiếp xúc thực sự kiểm soát quá trình oxy hóa ở mọi thời điểm và sự giãn nở thể tích cần thiết tại mặt tiếp xúc để bù đắp cho oxide đang mọc được cung cấp bởi dòng chảy nhớt (`viscous flow`) của lớp oxide `[6.14]`. Dòng chảy nhớt phụ thuộc thời gian của oxide, trong mô hình của họ, được dùng để giải thích sự phụ thuộc vào áp suất và nhiệt độ được trích xuất của các tham số trong mô hình của họ (`b` và `a`).

Mô hình được biểu diễn trong Phương trình `6.31` chưa được triển khai rộng rãi trong các chương trình mô phỏng quy trình. Các chương trình này nói chung vẫn dựa vào mô hình tuyến tính-parabol Deal-Grove. Tuy nhiên, cách tiếp cận vật lý được sử dụng trong `[6.13, 6.14]` thú vị vì các khái niệm về giãn nở thể tích và dòng chảy nhớt oxide cũng là các ý tưởng cơ bản được dùng để giải thích sự oxy hóa trên các bề mặt silicon không phẳng như chúng ta sẽ thấy trong Mục `6.5.7`.

Một cách tiếp cận khác để mô hình hóa động học oxy hóa gần đây đã được Han và Helms đề xuất `[6.15]`. Họ chỉ ra rằng một khối lượng lớn dữ liệu oxy hóa bao gồm chế độ mỏng `O₂` khô, có thể được mô hình hóa bởi một biểu thức có dạng

---

> **[Công thức toán]**
>
> $$
> \frac{dx_O}{dt} = \frac{B_1}{2x_O + A_1} + \frac{B_2}{2x_O + A_2}
> \tag{6.32}
> $$

---

Hai số hạng đại diện cho các quá trình oxy hóa song song, có thể là `O₂` và `O` khuếch tán qua `SiO₂` song song với nhau, hoặc có thể là `O₂` và các nút trống oxy. Loại khuếch tán và phản ứng song song này lần đầu tiên được đề xuất bởi Hirabayashi và Iwamura `[6.16]`, để mô hình hóa các oxy hóa `O₂/HCl`, một chủ đề chúng ta sẽ quay lại sau trong Mục `6.5.6`. Tất cả các hằng số tốc độ trong Phương trình `6.32` đều được tìm thấy phù hợp với các biểu thức Arrhenius có dạng

---

> **[Công thức toán]**
>
> $$
> B_1 = C\exp(-E_A/kT)
> \tag{6.33}
> $$

---

với các giá trị được cho trong **Bảng 6.3** dưới đây cho oxy hóa `O₂` khô.

---

> **[Bảng thông số]**

| | `B₁` | `B₁/A₁` | `B₂` | `B₂/A₂` |
|---|---|---|---|---|
| `C` | `6,5 × 10⁹ nm² min⁻¹` | `∞` | `2,6 × 10⁸ nm² min⁻¹` | `8,3 × 10⁷ nm min⁻¹` (111)<br>`2,6 × 10⁷ nm min⁻¹` (100) |
| `EA` | `2,2 eV` | — | `1,6 eV` | `1,9 eV` |

**Bảng 6.3:** Các hằng số tốc độ thực nghiệm cho mô hình oxy hóa song song của Han và Helms `[6.15]`.

---

Ngoại trừ các giá trị `B₂/A₂`, tất cả các con số trong **Bảng 6.3** áp dụng cho cả hướng silicon `(111)` lẫn `(100)`. Lưu ý rằng không có giá trị nào được đưa ra cho `B₁/A₁` vì Han và Helms thấy rằng việc đặt số hạng này bằng `∞` (`A₁ = 0`) tạo ra sự phù hợp hợp lý với thực nghiệm. Điều này có lẽ hàm ý rằng bất kỳ quá trình nào mà số hạng thứ nhất trong Phương trình `6.32` đại diện, phản ứng mặt tiếp xúc gắn với quá trình đó là rất nhanh. Tích phân `6.32` tạo ra một biểu thức dạng đóng cho chiều dày oxide theo thời gian

---

> **[Công thức toán]**
>
> $$
> (x_O^2 - x_i^2) + C(x_O - x_i) - G\ln\!\left(\frac{2x_O + F}{2x_i + F}\right) = Et
> \tag{6.34}
> $$
>
> trong đó:
>
> $$
> C = \frac{A_1 B_1 + A_2 B_2}{B_1 + B_2}, \quad
> E = B_1 + B_2, \quad
> F = \frac{A_1 B_2 + A_2 B_1}{B_1 + B_2}, \quad
> G = \frac{B_1 B_2 (A_1 - A_2)^2}{2(B_1 + B_2)^2}
> $$

---

Như đã đề cập ở trên, Han và Helms thấy rằng họ có thể khớp dữ liệu thực nghiệm thỏa đáng với `A₁ = 0`, điều này làm đơn giản hóa các biểu thức này phần nào. Mô hình này chưa được áp dụng cho các oxy hóa `H₂O`. Tuy nhiên, mô hình tuyến tính-parabol đơn giản hoạt động khá tốt đối với `H₂O`, và đó thực ra chỉ là một trường hợp đặc biệt của Phương trình `6.32` trong đó chỉ một trong hai số hạng được sử dụng.

Một mô hình khác đã được đề xuất là do Ghez và van der Meulen `[6.17]`. Mô hình được thúc đẩy bởi một loạt các thí nghiệm oxy hóa được thực hiện bởi van der Meulen với các áp suất riêng phần khác nhau của `O₂` trong môi trường oxy hóa. Mô hình tuyến tính-parabol dự đoán rằng cả `B` lẫn `B/A` đều phải tỷ lệ tuyến tính với áp suất. (Đây là hệ quả của việc giả sử rằng Định luật Henry đúng trong quá trình hấp phụ chất oxy hóa vào `SiO₂` và rằng chỉ có chất phân tử tham gia vào sự vận chuyển qua oxide và phản ứng tại mặt tiếp xúc `Si/SiO₂`.) Các phép đo của van der Meulen chỉ ra rằng

---

> **[Công thức toán]**
>
> $$
> \frac{B}{A} \propto P^n
> \tag{6.35}
> $$

---

trong đó `n` tiến đến `0,5` ở nhiệt độ oxy hóa thấp và `1` ở nhiệt độ cao. (Ngược lại, `n` bằng `1` thực nghiệm đối với các oxy hóa `H₂O`, gợi ý rằng các giả thiết được đưa ra trong mô hình Deal-Grove chính xác hơn trong trường hợp đó.)

Để giải thích các kết quả của họ, Ghez và van der Meulen đề xuất một mô hình trong đó `O₂` phân tử được hấp thụ từ pha khí và khuếch tán qua `SiO₂` đến bề mặt silicon. Tại mặt tiếp xúc oxy hóa, hai phản ứng song song được đề xuất, một liên quan đến `O₂` phân tử và một liên quan đến `O` nguyên tử. Điều này dẫn đến một quy luật mọc phức tạp không có công thức giải tích đơn giản. Tuy nhiên, phản ứng `O` nguyên tử dẫn đến giá trị `n = 0,5` cho phản ứng mặt tiếp xúc; phản ứng `O₂` phân tử dẫn đến giá trị `n = 1`. Dữ liệu của van der Meulen do đó có thể được giải thích bằng cách giả sử rằng phản ứng nguyên tử chiếm ưu thế ở nhiệt độ thấp và phản ứng phân tử ở nhiệt độ cao. Chúng ta sẽ thảo luận các kết quả này cẩn thận hơn trong Mục `6.5.4`.

Các **Hình 6.23** và **6.24** so sánh các dự đoán của một số mô hình thay thế này với mô hình Deal-Grove. Các tham số mô hình cho các đồ thị này được lấy từ **Bảng 6.2** và **6.3** cho mô hình Deal-Grove và mô hình Han và Helms tương ứng. Đối với mô hình Reisman và cộng sự ở `800°C`, `a = 0,302 nm`, `b = 0,704` và `t₀ = 13,1 min`. Ở `1000°C`, `a = 3,02 nm`, `b = 0,701` và `t₀ = 1,26 min` `[6.13]`.

Ở `800°C` (**Hình 6.23**), các sự khác biệt trong các mô hình này đối với các oxide rất mỏng là rõ ràng. Các mô hình Han và Helms và Reisman và cộng sự đồng ý khá tốt với nhau và cả hai đều khớp tốt với dữ liệu thực nghiệm trong chế độ mỏng. Mô hình Deal-Grove không làm tốt cho các oxide mỏng ngay cả khi đặt `τ` bằng `8` giờ (giá trị mà Deal và Grove trích xuất trong công trình gốc của họ `[6.6]`). Chúng ta sẽ thấy trong Mục `6.5.3` dưới đây rằng mô hình Deal-Grove có thể được "sửa chữa" để làm tốt hơn trong chế độ mỏng `O₂` khô. Lưu ý rằng đối với các oxide dày hơn khoảng `20 nm`, cả ba mô hình đều hội tụ đến xấp xỉ cùng một kết quả, miễn là chúng ta sử dụng `τ = 8` giờ trong mô hình Deal-Grove.

---

**Hình 6.23:** So sánh ba mô hình oxy hóa cho oxy hóa `O₂` khô `1 atm` ở `800°C`.
















