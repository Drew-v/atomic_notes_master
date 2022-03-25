[Format your notes - Obsidian Help](https://help.obsidian.md/How+to/Format+your+notes)
```mermaid
graph TD;
	A-->B;
	A-->C;
	C-->B;
	C-->A;
	A-->D;
	C-->D;
```

```mermaid
sequenceDiagram
    Alice->>+John: Hello John, how are you?
    Alice->>+John: John, can you hear me?
    John-->>-Alice: Hi Alice, I can hear you!
    John-->>-Alice: I feel great!
```

First Header | Second Header 
------------ | ------------ 
Content from cell 1 | Content from cell 2 
Content in the first column | Content in the second column
```mermaid
classDiagram  
Class01 <|-- AveryLongClass : Cool  
Class03 *-- Class04  
Class05 o-- Class06  
Class07 .. Class08  
Class09 --> C2 : Where am i?  
Class09 --* C3  
Class09 --|> Class07  
Class07 : equals()  
Class07 : Object[] elementData  
Class01 : size()  
Class01 : int chimp  
Class01 : int gorilla  
Class08 <--> C2: Cool label
```

```mermaid
erDiagram  
 CUSTOMER ||--o{ ORDER : places  
 ORDER ||--|{ LINE-ITEM : contains  
 CUSTOMER }|..|{ DELIVERY-ADDRESS : uses
 ```
 