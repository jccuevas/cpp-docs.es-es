---
title: Compilar programas con atributos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- tlb files
- MIDL
- MIDL, linker output
- IDL files
- tlb files, building attributed programs
- .tlb files, building attributed programs
- IDL files, building
- attributes [C++], building type libraries and .idl files
- .tlb files
- .idl files, building
- type libraries, linker options for building
ms.assetid: 04997b5f-bf2c-46ec-b868-c4adebbef5f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9d87f95b456e3f99598f48e6ffa8ad29806aa168
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="building-an-attributed-program"></a>Compilar programas con atributos
Después de colocar los atributos de Visual C++ en el código fuente, puede que desee el compilador de Visual C++ para generar un archivo de biblioteca y .idl de tipo automáticamente. El siguientes opciones del vinculador ayudan a crear archivos .tlb y. idl:  
  
-   [/IDLOUT](../build/reference/idlout-name-midl-output-files.md)  
  
-   [/IGNOREIDL](../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)  
  
-   [/ MIDL](../build/reference/midl-specify-midl-command-line-options.md)  
  
-   [/TLBOUT](../build/reference/tlbout-name-dot-tlb-file.md)  
  
 Algunos proyectos contienen varios archivos .idl independientes. Estos se utilizan para generar dos o más archivos .tlb y, opcionalmente, enlazarlos en el bloque de recursos. Este escenario no se admite actualmente en Visual C++.  
  
 Además, el vinculador de Visual C++ darán como resultado toda la información de atributo relacionada con IDL en un único archivo MIDL. No habrá ninguna manera de generar dos bibliotecas de tipos a partir de un solo proyecto.  
  
## <a name="see-also"></a>Vea también  
 [Conceptos](../windows/attributed-programming-concepts.md)