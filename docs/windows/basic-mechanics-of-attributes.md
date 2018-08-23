---
title: Mecanismos básicos de atributos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++], inserting in code
- attributes [C++], about attributes
ms.assetid: dc2069c3-b9f3-4a72-965c-4e5208ce8e34
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 75f30fbe64251e0fbb7fdb48f1d0a628ec4563b8
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42601230"
---
# <a name="basic-mechanics-of-attributes"></a>Mecanismos básicos de los atributos

Hay tres maneras de insertar atributos en el proyecto. En primer lugar, se puede insertarlos manualmente en el código fuente. En segundo lugar, puede insertarlos mediante la cuadrícula de propiedades de un objeto en el proyecto. Por último, puede insertarlos utilizando a los distintos asistentes. Para obtener más información sobre el uso de la **propiedades** ventana y los distintos asistentes, vea [crear y administrar proyectos de Visual C++](../ide/creating-and-managing-visual-cpp-projects.md).

Como antes, cuando se compila el proyecto, el compilador analiza cada archivo de origen de C++, generar un archivo de objeto. Sin embargo, cuando el compilador encuentra un atributo, se puede analizar y comprueba su sintaxis. A continuación, el compilador llama dinámicamente un proveedor de atributos para insertar código o realizar otras modificaciones en tiempo de compilación. La implementación del proveedor es diferente según el tipo de atributo. Por ejemplo, los atributos relacionados con ATL se implementan mediante Atlprov.dll.

En la siguiente ilustración se muestra la relación entre el compilador y el proveedor de atributos.

![Comunicación de atributos del componente](../windows/media/vccompattrcomm.gif "vcCompAttrComm")

> [!NOTE]
> Uso de atributos no modifica el contenido del archivo de origen. Es el único momento en que el código generado del atributo está visible durante las sesiones de depuración. Además, para cada archivo de código fuente en el proyecto, puede generar un archivo de texto que muestra los resultados de la sustitución de atributos. Para obtener más información sobre este procedimiento, consulte [/Fx (combinar código insertado)](../build/reference/fx-merge-injected-code.md) y [depurar código insertado](/visualstudio/debugger/how-to-debug-injected-code).

Al igual que la mayoría de las construcciones de C++, los atributos tienen un conjunto de características que define su uso correcto. Esto se conoce como el contexto del atributo y se trata en la tabla de contexto de atributo para cada tema de referencia de atributo. Por ejemplo, el [coclase](../windows/coclass.md) atributo solo puede aplicarse a una clase o estructura existente, en contraposición a la [cpp_quote](../windows/cpp-quote.md) atributo, que se puede insertar en cualquier lugar dentro de un archivo de código fuente de C++.

## <a name="see-also"></a>Vea también

[Conceptos](../windows/attributed-programming-concepts.md)