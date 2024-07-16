
  1. Component Concept
    - Structure in component
        + props : Cho chép truyền dữ liệu từ bên ngoài vào bên  trong component, ý nghĩa của việc viết props là
        sẽ thay đổi yêu cầu mong muốn, so với code base ban đầu
        
        + emits : cho phép truyền dữ liệu từ thằng con về thằng cha ,bắt sự kiện thông qua event
        
        + watch : được sử dụng để theo dõi hoặc nhiều thuộc tính phản ứng với các dữ liệu thay đổi , và thực hiện hành động  khi giá trị của chúng thay đổi 

        + computed : bản chất là 1 attribute, cho phép xử lý logic bên trong, dùng nó khi muốn biến đổi một dữ liệu
                     có sẵn sang một dữ liệu mới 