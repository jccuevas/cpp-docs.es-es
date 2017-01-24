---
title: "partial (Extensiones de componentes de C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "partial_CPP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "partial"
  - "C++/CX, partial"
ms.assetid: 43adf1f5-10c5-44aa-a66f-7507e2bdabf8
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# partial (Extensiones de componentes de C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La palabra clave `partial` habilita diferentes partes de la misma clase de referencia que se creará de forma independiente y en archivos diferentes.  
  
## Todos los runtimes  
 \(Esta característica de lenguaje solo se aplica a [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)].\)  
  
## [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]  
 Para una clase de referencia que tiene dos definiciones parciales, la palabra clave `partial` se aplica a la primera aparición de la definición y esto se hace normalmente por código que se genera automáticamente, de modo que un codificador humano no utilice la palabra clave habitualmente.  Para todas las definiciones parciales subsiguientes de la clase, omita el modificador `partial` de la palabra clave *clase\-clave* y el identificador de clase.  Cuando el compilador encuentra una clase de referencia y un identificador de clase previamente definidos, pero ninguna palabra clave `partial`, combina internamente todas las partes de la definición de clase de referencia en una definición.  
  
### Sintaxis  
  
```cpp  
  
partial class-key identifier {  
   /* The first part of the partial class definition. This is typically auto-generated*/  
}  
// ...  
class-key identifier {  
   /* The subsequent part(s) of the class definition. The same identifier is specified, but the "partial" keyword is omitted. */  
}  
  
```  
  
### Parámetros  
 *class\-key*  
 Una palabra clave que declara una clase o estructura que admite [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)].  O bien `ref class`, `value class`, `ref struct` o `value struct`.  
  
 *identifier*  
 Nombre de tipo definido.  
  
### Comentarios  
 Una clase parcial es compatible con los escenarios donde se modifica una parte de una definición de clase en un archivo y el software que genera código automático, por ejemplo, el diseñador XAML, modifica el código en la misma clase en otro archivo.  Mediante el uso de una clase parcial, puede evitar que el generador de código automático sobrescriba su código.  En un proyecto de Visual Studio, el modificador `partial` se aplica automáticamente al archivo generado.  
  
 Contenido: con dos excepciones, una definición de clase parcial puede contener cualquier elemento que la definición de clase completa pueda contener si la palabra clave `partial` se ha omitido.  Sin embargo, no puede especificar la accesibilidad de la clase \(por ejemplo, `public partial class X {…};`\), o `declspec`.  
  
 Los especificadores de Access utilizados en una definición de clase parcial para *identifier* no afectan a la accesibilidad predeterminada en una definición de clase parcial o completa subsiguiente para *identifier*.  Las definiciones alineadas de los miembros de datos estáticos están permitidas.  
  
 Declaración: Una definición parcial de una clase *identifier* presenta únicamente el nombre *identifier*, pero *identifier* no se puede usar de forma que requiere una definición de clase.  El nombre *identifier* no se puede utilizar para conocer el tamaño de *identifier*, o utilizar una base o miembro de *identifier* hasta después del compilador encuentra la definición completa de *identifier*.  
  
 Número y el orden: Puede haber definiciones de clase cero o más parciales para *identifier*.  Cada definición de clase parcial de *identifier* debe preceder léxico la una definición completa de *identifier* \(si hay una definición completa; si no, no se puede utilizar a menos que como si delantero\- esté declarado\) pero no necesita incluir declaraciones adelantadas de *identifier*.  Todas las claves de clase deben coincidir.  
  
 Definición completa: Actualmente la definición completa de la clase *identifier*, el comportamiento es el mismo que si la definición de *identifier* hubiera declarado todas las clases base, miembros, etc. en el orden en que se detectaron y se definieron en clases parciales.  
  
 Plantillas: Una clase parcial no puede ser una plantilla.  
  
 Genéricos: una clase parcial puede ser un genérico si la definición completa podría ser genérica.  Pero cada clase parcial y completa debe tener exactamente los mismos parámetros genéricos, como nombres de parámetros formales.  
  
 Para obtener más información sobre cómo utilizar la palabra clave de `partial` , vea [Clases parciales \(C\+\+\/CX\)](http://go.microsoft.com/fwlink/p/?LinkId=249023).  
  
### Requisitos  
 Opción del compilador: **\/ZW**  
  
## Common Language Runtime  
 \(Esta característica de lenguaje no se aplica a Common Language Runtime\).  
  
## Vea también  
 [Clases parciales \(C\+\+\/CX\)](http://go.microsoft.com/fwlink/p/?LinkId=249023)