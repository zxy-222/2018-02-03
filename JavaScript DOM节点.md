### JavaScript DOM 节点操作方法总结

- **节点类型主要有三种:元素节点、属性节点、文本节点。**

- **对于DOM操作的主要也就是围绕元素节点和属性节点的增、删、查、改。**

- #### 1、元素节点

  - **1、查**

    - 1、在对***DOM***进行增删查改之前，首先要找到对应的元素，方法如下：

      ```
      get ElementById() //得到单个节点
      get ElementsByTagName() //得到节点数组 NodeList
      get ElementsByName() //得到节点数组 NodeList
      ```

    - 2、***子节点***

      ```
      Node.childNodes //获取子节点列表NodeList；换行在浏览器中被算作了text节点，如果用这种方式获取节点列表，需要进行过滤
      Node.firstChild //返回第一个子节点
      Node.lastChild //返回最后一个子节点
      ```

    - ***3、父节点***

      ```
      Node.parentNode //返回父节点
      Node.ownerDocument//返回祖先节点
      ```

    - ***4、同胞节点***

      ```
      Node.previousSibling //返回前一个节点，如果没有则返回null
      Node.nextSibling  // 返回下一个节点
      ```

  - **2、增**

    - 1、新增节点首先要创建节点，然后将新建的节点插入***DOM***中

    - 2、***创建节点***

      ```
      createElement()   //按照指定的标签名创建一个新的元素节点
      ```

      - 创建代码片段(避免频繁刷新DOM，可以先创造代码片段，完成所有节点操作之后统一添加到DOM中)

        ```
        createElement() 
        ```

    - ***3、复制节点***

      ```
      cloneNode = Node.cloneNode(boolean) //只有一个参数，传入布尔值，true表示复制该节点下的所有子节点；false表示只复制该节点
      ```

    - ***4、插入节点***

      ```
      /*插入node*/
      parentNode.appendChild(childNode); //将新节点追加到子节点列表的末尾
      parentNode.insertBefore(newNode,targetNode); //将newNode插入到target Node之前

      /*插入html代码*/
      node.insertAdjacentHTM('beforeBegin',html); //在该元素之前插入代码
      node.insertAdjacentHTM('afterBegin',html); //在该元素的第一个子元素之前插入代码
      node.insertAdjacentHTM('beforeEnd',html); //在该元素的最后一个元素之后插入代码
      node.insertAdjacentHTM('afterEnd',html); //在该元素之后插入代码
      ```

    - ***5、替换节点***

      ```
      parentNode.replace(newNode,targetNode);//使用newNode替换targetNode
      ```

  - **3、删**

    - ***1、移除节点***

      ```
      parentNode.removeChild(childNode); //移除目标节点
      node.parentNode.removeChild(node); //在不清楚父节点的情况下使用
      ```

- #### 2、属性节点

  - **1、操作属性节点，就是对DOM样式进行增删查改。对于行内样式、外部样式有不同的操作方法；各种方法获得的样式也有可读可写和只读之分。**

  - **2、直接获取CSS样式**

    ```
    node.style.color   //可读可写
    ```

    - ***1、style本身属性和方法***

      ```
      node.style.cssText   //获取node行内样式字符串
      node.style.length     //获取行内样式个数
      node.style.item(0)    //获取指定位置的样式
      ```

    - ***2、获取和修改元素样式***

      - 1、H5为元素提供了一个新的属性:classList来实现对元素样式标的增删查改。

        ```
        node.classList.add(value);   //为元素添加指定的类
        node.classList.contains(value); //判断元素是否含有指定的类，如果存在返回true
        node.classList.remove(value); //删除指定的类
        node.classList.toggle(value); // 有就删除，没有就添加指定类
        ```

      - 2、修改DOM特性的方法

        ```
        Node.getAttribute('id') //获取
        Node.setAttribute('id')//设置
        Node.removeAttribute() //移除
        Node.attributes       //获取DOM全部特性
        ```

        ​

