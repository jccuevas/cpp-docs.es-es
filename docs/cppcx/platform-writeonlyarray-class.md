---
title: "Platform::WriteOnlyArray (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
s.suite: 
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::WriteOnlyArray"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::WriteOnlyArray (Clase)"
ms.assetid: 92d7dd56-ec58-4b8c-88ba-9c903668b687
caps.latest.revision: 11
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 11
---
# Platform::WriteOnlyArray (Clase)
Representa una matriz unidimensional que se utiliza como parámetro de entrada cuando el llamador pasa una matriz para el método que se va a rellenar.  
  
 Esta clase ref se declara como privada en vccorlib.h; por consiguiente, no se emite en los metadatos y solo se puede usar desde C\+\+. Esta clase está diseñada únicamente para su uso como un parámetro de entrada que recibe una matriz que el llamador ha asignado. No se puede crear desde el código de usuario. Permite a un método de C\+\+ escribir directamente en dicha matriz, patrón que se conoce como *FillArray*. Para obtener más información, consulta [Array y WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).  
  
## Sintaxis  
  
```cpp  
private ref class WriteOnlyArray<T, 1>  
```  
  
## Miembros  
  
### Métodos públicos  
 Estos métodos tienen accesibilidad interna, es decir, solo están accesibles desde la aplicación o componente de C\+\+.  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[WriteOnlyArray::begin \(Método\)](../cppcx/writeonlyarray-begin-method.md)|Un iterador que apunta al primer elemento de la matriz.|  
|[WriteOnlyArray::Data \(Propiedad\)](../cppcx/writeonlyarray-data-property.md)|Puntero al búfer de datos.|  
|[WriteOnlyArray::end \(Método\)](../cppcx/writeonlyarray-end-method.md)|Un iterador que apunta a uno más allá del último elemento de la matriz.|  
|[WriteOnlyArray::FastPass \(Propiedad\)](../cppcx/writeonlyarray-fastpass-property.md)|Indica si la matriz puede usar el mecanismo FastPass, que es una optimización realizada por el sistema de manera transparente. No utilices esto en tu código|  
|[WriteOnlyArray::Length \(Propiedad\)](../cppcx/writeonlyarray-length-property.md)|Devuelve el número de elementos de la matriz.|  
|[WriteOnlyArray::set \(Función\)](../cppcx/writeonlyarray-set-function.md)|Establece el elemento especificado en el valor indicado.|  
  
## Jerarquía de herencia  
 `WriteOnlyArray`  
  
## Requisitos  
 Opción del compilador: **\/ZW**  
  
 **Metadatos:** Platform.winmd  
  
 **Espacio de nombres:** Plataforma  
  
## Vea también  
 [Espacio de nombres de plataforma \(NOTINBUILD\)](http://msdn.microsoft.com/es-es/f3ce3eab-028c-4204-ba9f-9ab8af17c8c4)   
 [Crear componentes de Windows en tiempo de ejecución en C\+\+](http://msdn.microsoft.com/library/5b7251e6-4271-4f13-af80-c1cf5b1489bf)