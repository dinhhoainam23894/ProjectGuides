# Những hướng dẫn cho Project 

Trong khi phát triển một dự án mới giống như bạn đang lăn trên nền cỏ xanh, 
thì bảo trì giống như một cơn ác mộng với những người khác. Dưới đây là một số
 những hướng dẫn chúng tôi đã tìm, viết và thu thập, những thứ mà chúng tôi nghĩ rằng thực sự 
 tốt cho các dự án Javascript ở đây tại [elsewhen](http://elsewhen.co/). Nếu bạn muốn gửi chia sẻ
 những điều tốt hơn hay nghĩ rằng những hướng dẫn của chúng tôi nên loại bỏ, 
 [Hãy thoải mái chia sẻ với chúng tôi](http://makeapullrequest.com/)
 
## 5. Thử nghiệm

* Nên có một môi trường `thử nghiệm` nếu nó cần thiết.

    _Tại sao:_
    > Trong khi thi thoảng việc [End to end testing](https://viblo.asia/p/what-is-end-to-end-testing-znmMd0P6Mr69) 
    ở chế độ `production` có vẻ là đủ thì nó lại có vài ngoại lệ:
    Ví dụ như bạn có thể không muốn cho phép việc phân tích thông tin trong chế độ 'production' và làm rác
    bảng điều khiển của một ai đó bởi các dữ liệu test. Những ví dụ khác như việc
    API của bạn có thể có những giới hạn tỉ lệ trong  chế độ`production` và chặn các việc gọi phương thức test sau khi đã
    có một lượng lớn request đã được đưa ra.

* Đặt các file thử nghiệm ngay bên cạnh các module đã test ~~mà sử dụng `*.test.js` hoặc `*.spec.js` để đặt tên 
theo quy ước, ví dụ như `moduleName.spec.js`~~  **bằng cách sử dụng quy ước đặt tên `*.test.js` hoặc `*.spec.js`, như `moduleName.spec.js`** (using `*.test.js` or `*.spec.js` naming convention, like `moduleName.spec.js`.).

    _Tại sao:_
    > Bạn không muốn đào sâu vào một cấu trục thư mục để tìm một nơi thử nghiệm [Xem thêm...](https://hackernoon.com/structure-your-javascript-code-for-testability-9bc93d9c72dc) 

* Đưa các tập tin kiểm tra bổ sung của bạn vào một thư mục thử nghiệm riêng biệt để tránh nhầm lẫn.    
    
    _Tại sao:_
    > Một vài file thử nghiệm không có quan hệ cụ thể với bất kì một file thực thi nào. Bạn phải đưa nó vào trong 1 thư mục
    ~~nơi mà hầu hết được tìm~~ **có nhiều khả năng được tìm thấy** (most likely to be found by) bởi các developer: thư mục `__test__`. Tên `__test__` hiện tại cũng là chuẩn và được sử dụng bởi
    hầu hết các Framework JavaScript thử nghiệm.
    
* Viết những đoạn mã có thể thử nghiệm, tránh những sai sót, viết các hàm thuần túy.

    _Tại sao:_ 
    
    >Bạn muốn kiểm tra một logic kinh doanh như các đơn vị riêng biệt. Bạn phải
    "giảm thiểu tác động ngẫu nhiên và các quy trình không xác định đối với code của bạn"
    [Xem thêm...](https://medium.com/javascript-scene/tdd-the-rite-way-53c9b46f45e3)
    > Một hàm thuẩn là một hàm mà luôn luôn trả ~~về cùng một đầu ra~~ **về cùng một đầu ra cho cùng một đầu vào** (the same output for the same input).
    Ngược lại một hàm không thuần là một hàm mà có những tác động bên ngoài hoặc phụ thuộc vào điều kiện từ bên ngoài để
    tạo ra giá trị. Nó khiến chúng khó lường trước được [Xem thêm...](https://hackernoon.com/structure-your-javascript-code-for-testability-9bc93d9c72dc)

* Sử dụng một bộ kiểm tra loại tĩnh

    _Tại sao:_
    > Thi thoảng bạn có lẽ cần một bộ kiểm tra Static. Nó mang đến a mức độ chắc chắn về độ tin tưởng cho đoạn code 
    của bạn [Xem thêm...](https://medium.freecodecamp.org/why-use-static-types-in-javascript-part-1-8382da1e0adb)
    
* Chạy thử nghiệm ở dưới local trước khi tạo ra bất kì pull request nào đến `develop`
    
    _Tại sao:_
    > Bạn không muốn trở thành người mà gây ra việc tạo nhánh production-ready thất bại.
    Chạy thử nghiệm sau khi bạn đã `rebase` và trước khi đẩy feature-branch lên một remote repository
   
* Kiểm chứng những thử nghiệm bao gồm các phần hướng dẫn liên quan trong file README.md`.
    
    _Tại sao:_
    > Đây là một ghi chú tiện dụng mà bạn nên để lại cho các developer khác hoặc chuyên gia DevOps hoặc QA hoặc cho
    bất kì ai đủ may mắn khi làm việc với code của bạn
   
<a name="structure-and-naming"></a>

## 6. Cấu trúc và đặt tên

![Cấu trúc và đặt tên](https://github.com/wearehive/project-guidelines/raw/master/images/folder-tree.png)
* Tổ chức các file của bạn theo tính năng sản phẩm chứ không phải theo vai trò như sau: features / pages / components. Bên cạnh đó, đặt các file thử nghiệm ngay cạnh việc triển khai.
    
    **Cách tổ chức không tốt**

    ```
    .
    ├── controllers
    |   ├── product.js
    |   └── user.js
    ├── models
    |   ├── product.js
    |   └── user.js
    ```

    **Cách tổ chức tốt**

    ```
    .
    ├── product
    |   ├── index.js
    |   ├── product.js
    |   └── product.test.js
    ├── user
    |   ├── index.js
    |   ├── user.js
    |   └── user.test.js
    ```

    _Tại sao phải như vậy:_
    > Thay vì một danh sách dài các file, bạn sẽ tạo ra các module nhỏ mà gói gọn một trách nhiệm, nhiệm vụ bao gồm thử nghiệm nó và .v.v.. Sẽ dễ dàng hơn trong việc điều hướng và tất cả mọi thứ có thể được tìm chỉ bằng cái chớp mắt
    
* Đưa file test của bạn đến một thư mục test để tránh việc nhầm lẫn
    
    _Tại sao phải làm vậy:_
        > Nó sẽ tiết kiệm thời gian cho các Developer khác hoặc DevOps khác trong team bạn
    
    * Sử dụng một folder `./config` và đừng tạo ra các file config khác nhau trong các môi trường khác nhau 
    
        _Tại sao phải làm vậy:_
        > Khi bạn chia nhỏ file config cho nhiều mục đích khác nhau (database, API và .v.v..); đưa chúng vào 1 thư mục với cái tên có thể nhận biết ví dụ
        các giá trị được sử dụng trong các file config đang nhẽ nên được cung cấp bởi môi trường các biến. [Xem thêm...](https://medium.com/@fedorHK/no-config-b3f1171eecd5)
       
    * Đưa các đoạn mã script vào thư mục `./scripts`. Điều đó bao gồm cả các đoạn mã `bash` script và `node` script.
    
        _Tại sao phải làm vậy:_
        > 
        > Rất có thể bạn có thể kết thúc với nhiều kịch bản, xây dựng sản xuất, phát triển xây dựng, cơ sở dữ liệu feeders, đồng bộ hóa cơ sở dữ liệu và như vậy.   
    
    * Đặt các __build ouput__ trong thư mục `./build`. Thêm `build/` và `.gitignore` 
        _Tại sao phải làm vậy:_
        > Đặt tên chúng theo ý bạn, có thể là `dist` chẳng hạn. Nhưng đảm bảo rằng chúng phù hợp vs team của bạn. Những gì nhận được đã được tạo ra (đóng gọi, biên dịch, chuyển giao) hoặc được di chuyển đến. Những gì bạn tạo, các thành viên của nhóm cũng nên tạo cùng, vì vậy không có mục đích gì để commit chúng lên git trừ phi bạn muốn.
        
    <a name="code-style"></a>
    
## 7. Code style

![Code style](/images/code-style.png)

<a name="code-style-check"></a>
### 7.1 Một vài hướng dẫn về code style

* Sử dụng cú pháp JavaScript ở chương 2 và cao cấp hơn (hiện đại hơn) cho dự án mới. Với những dự án cũ còn sử dụng những cú pháp trước đó thì chỉ sử dụng cú pháp mới trừ khi bạn muốn nâng cấp nó.
    
    _Tại sao nên như vậy:_
    > Tất cả điều đó phụ thuộc vào bạn. Chúng tôi sử dụng chúng để tận dụng những thuận tiện của cú pháp mới. Chương 2 nhiều khả năng trở thành một phần của __spec__ với những sửa đổi nhỏ
    
* Hãy kiểm tra code style trong quá trình xây dựng hệ thống.

    _Tại sao phải như vậy:_
    > Phá vỡ những gì bạn đã xây dựng là một cách áp dụng code style và trong code của bạn. Nó sẽ giúp bạn làm code bớt tính nghiêm trọng. Hãy thực hiện điều đó ở cả client lẫn server. [Xem thêm...](https://www.robinwieruch.de/react-eslint-webpack-babel/)
    
* Sử dụng [ESLint - Pluggable JavaScript linter](http://eslint.org/) để áp dung code style

    _Tại sao phải làm vậy:_
    > Chúng tôi đơn giản là thích `eslint` hơn và bạn không cần phải làm vậy. Nó có nhiều quy tắc được hỗ trợ, khả năng cấu hình các quy tắc và khả năng thêm các quy tắc tùy chỉnh.

* Chúng tôi sử dụng [Airbnb JavaScript Style Guide](https://github.com/airbnb/javascript) cho JavaScript, [Xem thêm](https://www.gitbook.com/book/duk/airbnb-javascript-guidelines/details). Sử dụng JavaScript Style Guide được yêu cầu bởi dự án hoặc các thành viên trong team.

* Chúng tôi sử dụng [Flow type style check rules for ESLint](https://github.com/gajus/eslint-plugin-flowtype) khi sử đang sử dụng [FlowType](https://flow.org/).

    _Tại sao lại làm như vậy:_
    > Flow giới thiệu vài cú pháp mà cũng cần phải làm theo kiểu mã nhất định và được kiểm tra

* Sử dụng `.eslintignore` để loại trừ các file hoặc thư mục ra khỏi việc kiểm tra code style.

    _Tại sao phải làm vậy:_
    > Bạn không nhất thiết phải làm bẩn code của mình bằng việc sử dụng các comment của `eslint-disable` bất kể khi nào bạn cần loại bỏ các file khỏi bị kiểm tra code style.

* Loại bỏ các comment `eslint` đã bị vô hiệu hóa trc khi tạo ra một Pull Request 

    _Tại sao phải làm như vậy_
    > Sẽ thật bình thường khi vô hiệu hóa việc kiểm tra code style khi đang làm việc trong một khối code để có thể tập trung hơn vào logic. Hãy nhớ loại bỏ hết các comment `eslint-disable` và theo các nguyên tắc của nó.

* Phụ thuộc vào kích thước của nhiệm vụ hãy sử dụng comment `//TODO` hoặc mở một ticket.

    _Tại sao phải làm như vậy_
    > Vì bạn có thể nhắc lại bản thân và những người khác về một nhiệm vụ (Ví dụ như sắp xếp lại một chức năng hoặc cập nhật nhận xét). Đối với nhiệm vụ lớn hơn hãy sử dụng `//TODO(#3456)` mà đã được áp dụng bởi quy tắc __lint__ và con số kia là một open ticket

* Luôn luôn comment và giữ mối liên quan khi code thay đổi. Loại bỏ các khối code đã được comment.
    
    _Tại sao phỉa làm như vậy:_
    > Code của bạn nên dễ đọc nhất có thể, bạn nên loại bất kể điều gì làm mất tập trung. Nếu bạn sắp xếp lại một function, đưng comment function cũ mà hãy bỏ nó đi.

* Tránh những comment, log hoặc tên không liên quan hoặc hài hước.    

    _Tại sao phải như vậy:_
    > Trong khi quá trình xây dựng của bạn có thể bị loại bỏ chúng, đôi khi mã nguồn của bạn có thể được bàn giao cho công ty / khách hàng khác và __they may not share the same banter__

* Tạo ra các tên có thể tìm kiếm vs ý nghĩa khác nhau và tránh rút gọn tên. Đối với những function sử dụng nhiều, hãy đặt tên mô tả. Tên của một function nên là một động từ hoặc cụm động từ, và nó cần nói nên được ý định của nó
    
    _Tại sao phải vậy:_
    > Điều đó tạo ra môt sự tự nhiên nhất khi đọc mã nguồn.

* Tổ chức các function của bạn trong một file theo nguyên tắc __step-down__. Các function ở mức độ cao hơn nên đươc để lên đầu và thấp hơn thì để ở dứoi

    _Tại sao phải làm như vậy:_
    > Điều đó tạo ra môt sự tự nhiên nhất khi đọc mã nguồn.

<a name="enforcing-code-style-standards"></a>
### 7.2 Áp dụng các tiêu chuẩn code style

* Sử dụng một file [.editorconfig](http://editorconfig.org/) nó sẽ giúp developer định nghĩa và bảo trì code một cách nhất quán giữa các editors và IDES cho project của bạn.

    _Tại sao phải làm như vậy:_
    > Các dự án EditorConfig bao gồm một file định dạng để xác định code style và một tập hợp các plugin trình soạn thảo text cho phép biên tập viên đọc định dạng tệp và tuân theo các kiểu được xác định. Các tập tin EditorConfig có thể đọc được dễ dàng và chúng hoạt động độc đáo với các hệ thống điều khiển phiên bản.

* Cài đặt cho editor của bạn thông báo cho bạn các lỗi về code style. Sử dụng [eslint-plugin-prettier](https://github.com/prettier/eslint-plugin-prettier) và [eslint-config-prettier](https://github.com/prettier/eslint-config-prettier) với những cấu hình ESLint có sẵn. [Xem thêm...](https://github.com/prettier/eslint-config-prettier#installation)

* Xem xét sử dụng Git hook.

    _Tại sao phải làm vậy:_
    > Git hooks làm tăng đáng kể năng suất của một developer. Thực hiện thay đổi, commit và push vào môi trường staging hoặc production mà không sợ phá vỡ cấu trúc. [Xem thêm ...] (http://githooks.com/)

* Sử dụng Prttier với một __precommit hook__

    _Tại sao phải làm như vậy:_
    > Mặc dù `prettier` có thể rất mạnh, nhưng nó không hiệu quả khi chạy nó đơn giản như một nhiệm vụ của NPM mỗi lần để định dạng mã. Đây là nơi `lint-staged` (và `husky`) thực hiện kế thừa. Đọc thêm về cách cấu hình `lint-staged` [ở đây] (https://github.com/okonet/lint-staged#configuration) và về cách cấu hình` husky` [ở đây] (https://github.com/typicode/husky ).

<a name="logging"></a>    
    