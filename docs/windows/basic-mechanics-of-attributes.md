---
title: "Mecanismos básicos de los atributos | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- attributes [C++], inserting in code
- attributes [C++], about attributes
ms.assetid: dc2069c3-b9f3-4a72-965c-4e5208ce8e34
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 99771e798e4957de5ff69601a5d3494e5fcacc35
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="basic-mechanics-of-attributes"></a>Mecanismos básicos de los atributos
Hay tres formas de insertar atributos en el proyecto. En primer lugar, se puede insertarlos manualmente en el código fuente. En segundo lugar, puede insertarlos mediante la cuadrícula de propiedades de un objeto en el proyecto. Por último, puede insertarlos utilizando a los distintos asistentes. Para obtener más información sobre el uso de la ventana Propiedades y los distintos asistentes, vea [crear y administrar proyectos de Visual C++](../ide/creating-and-managing-visual-cpp-projects.md).  
  
 Como antes, cuando se compila el proyecto, el compilador analiza cada archivo de fuente de C++, generar un archivo de objeto. Sin embargo, cuando el compilador encuentra un atributo, se analiza y comprueba su sintaxis. A continuación, el compilador llama dinámicamente un proveedor de atributos para insertar código o realizar otras modificaciones en tiempo de compilación. La implementación del proveedor de varía según el tipo de atributo. Por ejemplo, los atributos relacionados con ATL se implementan mediante Atlprov.dll.  
  
 En la siguiente ilustración se muestra la relación entre el compilador y el proveedor de atributos.  
  
 ![Comunicación de atributos de componente](../windows/media/vccompattrcomm.gif "vcCompAttrComm")  
  
> [!NOTE]
>  Uso de atributos no modifica el contenido del archivo de origen. Es la única vez que el código de atributo generado está visible durante las sesiones de depuración. Además, para cada archivo de origen en el proyecto, puede generar un archivo de texto que muestra los resultados de la sustitución de atributos. Para obtener más información acerca de este procedimiento, consulte [/Fx (combinar código insertado)](../build/reference/fx-merge-injected-code.md) y [depurar código insertado](/visualstudio/debugger/how-to-debug-injected-code).  
  
 Al igual que la mayoría de las construcciones de C++, atributos tienen un conjunto de características que define su uso correcto. Esto se conoce como el contexto del atributo y se trata en la tabla de contexto de atributo para cada tema de referencia de atributo. Por ejemplo, el [coclase](../windows/coclass.md) atributo solo puede aplicarse a una clase o estructura existente, en contraposición a la [cpp_quote](../windows/cpp-quote.md) atributo, que puede insertar en cualquier parte dentro de un archivo de código fuente de C++.  
  
## <a name="see-also"></a>Vea también  
 [Conceptos](../windows/attributed-programming-concepts.md)