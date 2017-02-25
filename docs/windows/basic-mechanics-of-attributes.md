---
title: "Basic Mechanics of Attributes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "attributes [C++], inserting in code"
  - "attributes [C++], about attributes"
ms.assetid: dc2069c3-b9f3-4a72-965c-4e5208ce8e34
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Basic Mechanics of Attributes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

hay tres maneras de insertar atributos en el proyecto.  Primero, puede incrustarlos manualmente en el código fuente.  En segundo lugar, puede incrustarlos mediante la cuadrícula de propiedades de un objeto del proyecto.  Finalmente, puede incrustarlos mediante diversos asistentes.  Para obtener más información sobre cómo utilizar la ventana Propiedades y los diversos asistentes, vea [Crear y administrar los proyectos de Visual C\+\+](../ide/creating-and-managing-visual-cpp-projects.md).  
  
 A partir de Visual C\+\+ .NET, el compilador reconoce la presencia de atributos en un archivo de código fuente y puede analizarlos y comprobar dinámicamente durante la compilación.  
  
 Como antes de que, cuando se compila el proyecto, el compilador analiza cada archivo de código fuente de C\+\+, genera un archivo objeto.  sin embargo, cuando el compilador encuentra un atributo, se analiza y se comprueba sintácticamente.  El compilador llama dinámicamente un proveedor de atributo para insertar código o crear otras modificaciones en tiempo de compilación.  La implementación del proveedor difiere en función del tipo de atributo.  Por ejemplo, los atributos ATL\-relacionados se implementan mediante Atlprov.dll.  
  
 La ilustración siguiente se muestra la relación entre el compilador y el proveedor del atributo.  
  
 ![Comunicación de atributos de componentes](../windows/media/vccompattrcomm.png "vcCompAttrComm")  
  
> [!NOTE]
>  El uso del atributo no modifica el contenido del archivo de código fuente.  La única vez que el código generado del atributo es visible está durante las sesiones de depuración.  Además, para cada archivo de código fuente del proyecto, puede generar un archivo de texto que muestra los resultados de sustitución de atributo.  Para obtener más información sobre este procedimiento, vea [\/Fx \(Código insertado de combinación\)](../build/reference/fx-merge-injected-code.md) y [Código insertado de depuración](../Topic/How%20to:%20Debug%20Injected%20Code.md).  
  
 Como la mayoría de las construcciones de C\+\+, los atributos tienen un conjunto de características que defina el uso apropiado.  Se conoce como contexto de atributo y se soluciona esta en la tabla de contexto de atributo para cada tema de referencia del atributo.  Por ejemplo, el atributo de [CoClass](../windows/coclass.md) sólo se puede aplicar a una clase o estructura existente, en comparación con el atributo de [cpp\_quote](../Topic/cpp_quote.md) , que se puede insertar en cualquier parte del archivo de código fuente de C\+\+.  
  
## Vea también  
 [Concepts](../windows/attributed-programming-concepts.md)