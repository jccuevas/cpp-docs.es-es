---
title: "La vinculaci&#243;n de miembros integrales const est&#225;ticos ya no es literal | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "constantes, declarar"
  - "expresiones constantes de tipo entero"
  - "atributo literal [C++]"
ms.assetid: d2a5e3d2-ffb0-4b61-8114-bec5993a1195
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# La vinculaci&#243;n de miembros integrales const est&#225;ticos ya no es literal
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La declaración de un miembro constante de una clase ha cambiado de Extensiones administradas para C\+\+ a [!INCLUDE[cpp_current_long](../dotnet/includes/cpp_current_long_md.md)].  
  
 Aunque todavía se admiten los miembros enteros `static const`, su atributo de vinculación ha cambiado.  Su atributo de vinculación anterior ahora lo lleva un miembro entero literal.  Por ejemplo, considere la siguiente clase de Extensiones administradas:  
  
```  
public __gc class Constants {  
public:  
   static const int LOG_DEBUG = 4;  
};  
```  
  
 Esto genera los siguientes atributos CIL subyacentes para el campo \(tenga en cuenta el atributo literal\):  
  
```  
.field public static literal int32   
modopt([Microsoft.VisualC]Microsoft.VisualC.IsConstModifier) STANDARD_CLIENT_PRX = int32(0x00000004)  
```  
  
 Mientras que esto aún se compila en la nueva sintaxis:  
  
```  
public ref class Constants {  
public:  
   static const int LOG_DEBUG = 4;  
};  
```  
  
 ya no emite el atributo literal y, por consiguiente, el tiempo de ejecución del CLR no lo ve como una constante:  
  
```  
.field public static int32 modopt([Microsoft.VisualC]Microsoft.VisualC.IsConstModifier) STANDARD_CLIENT_PRX = int32(0x00000004)  
```  
  
 Para tener el mismo atributo literal entre lenguajes, la declaración se debería cambiar al miembro de datos `literal` recientemente compatible, como sigue:  
  
```  
public ref class Constants {  
public:  
   literal int LOG_DEBUG = 4;  
};  
```  
  
## Vea también  
 [Declaraciones de miembros en una clase o interfaz \(C\+\+\/CLI\)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)   
 [literal](../windows/literal-cpp-component-extensions.md)