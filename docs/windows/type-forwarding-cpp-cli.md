---
title: "Reenv&#237;o de tipos (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "reenvío de tipos, Visual C++"
ms.assetid: ae730b69-0c27-41cc-84e1-3132783866ea
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Reenv&#237;o de tipos (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

*El reenvío de tipos* permite mover un tipo a partir de un ensamblado \(A\) en otro ensamblado \(B\), como, no es necesario volver a compilar los clientes que utilizan el ensamblado A.  
  
## Todas las plataformas  
 Esta característica no se admite en todos los runtimes.  
  
## Windows en tiempo de ejecución  
 Esta característica no se admite en [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)].  
  
### Requisitos  
 Opción del compilador: **\/ZW**  
  
## Common Language Runtime  
 El ejemplo de código siguiente muestra cómo utilizar el reenvío de tipos.  
  
### Sintaxis  
  
```  
#using "new.dll"  
[assembly:TypeForwardedTo(type::typeid)];  
```  
  
### Parámetros  
 `new`  
 El ensamblado que se está moviendo la definición de tipo.  
  
 `type`  
 Definición de tipo cuya mueve en otro ensamblado.  
  
### Comentarios  
 Después de que un componente \(ensamblado\) send y está siendo utilizado por aplicaciones cliente, puede utilizar el reenvío de tipos para pasar un tipo de componente \(ensamblado\) a otro ensamblado, envía el componente actualizado \(y cualquier ensamblados adicionales necesarios\), y las aplicaciones cliente funcionarán sin volver a compilar.  
  
 El tipo que reenvía sólo funciona para los componentes a los que hace referencia por aplicaciones existentes.  Al recompilar una aplicación, debe haber referencias adecuadas de ensamblado para los tipos utilizados en la aplicación.  
  
 Para reenviar un tipo \(tipo A\) de un ensamblado, debe agregar el atributo de `TypeForwardedTo` para ese tipo, así como una referencia de ensamblado.  El ensamblado que hace referencia debe contener uno de los siguientes:  
  
-   La definición del A. escrito.  
  
-   Un atributo de `TypeForwardedTo` para el tipo En, así como una referencia de ensamblado.  
  
 Ejemplos de tipos que pueden ser incluyen reenviada:  
  
-   clases de referencia  
  
-   clases de valor  
  
-   enumeraciones  
  
-   interfaces  
  
 No puede reenviar los tipos siguientes:  
  
-   Tipos genéricos  
  
-   Tipos nativos  
  
-   Tipos anidados \(si desea reenviar un tipo anidado, debe reenviar envuelve\)  
  
 Puede reenviar un tipo en un ensamblado creado en cualquier lenguaje orientado a Common Language Runtime.  
  
 Por lo tanto, si un archivo de código fuente que se utiliza para compilar el ensamblado A.dll contiene una definición de tipo \(`ref class MyClass`\), y desea mover esa definición de tipo al ensamblado B.dll, debe:  
  
1.  Mueva la definición de tipo de `MyClass` a un archivo de código fuente utilizado para compilar B.dll.  
  
2.  Compile el ensamblado B.dll  
  
3.  Elimine la definición de tipo de `MyClass` de código fuente utilizado para compilar A.dll, y reemplácelo con el siguiente:  
  
    ```  
    #using "B.dll"  
    [assembly:TypeForwardedTo(MyClass::typeid)];  
    ```  
  
4.  Compile el ensamblado A.dll.  
  
5.  Utilice A.dll sin volver a compilar las aplicaciones cliente.  
  
### Requisitos  
 Opción del compilador: **\/clr**