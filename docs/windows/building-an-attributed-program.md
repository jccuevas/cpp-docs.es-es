---
title: Compilar programas con atributos | Microsoft Docs
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
ms.openlocfilehash: 7909884a355ccad5e1bf9d18a38dd3e4690296ee
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42587512"
---
# <a name="building-an-attributed-program"></a>Compilar programas con atributos

Después de colocar los atributos de Visual C++ en el código fuente, puede el compilador de Visual C++ para generar un archivo .idl y de biblioteca de tipos para usted. Las siguiente opciones del vinculador ayudan a crear archivos .tlb y .idl:

- [/ IDLOUT](../build/reference/idlout-name-midl-output-files.md)

- [/IGNOREIDL](../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)

- [/ MIDL](../build/reference/midl-specify-midl-command-line-options.md)

- [/ TLBOUT](../build/reference/tlbout-name-dot-tlb-file.md)

Algunos proyectos contienen varios archivos .idl independientes. Estos se usan para generar dos o más archivos .tlb y, opcionalmente, enlazarlos con el bloque de recursos. Este escenario no se admite actualmente en Visual C++.

Además, el vinculador de Visual C++ generarán toda la información de atributos relacionados con el IDL en un único archivo MIDL. No habrá ninguna manera de generar dos bibliotecas de tipos desde un solo proyecto.

## <a name="see-also"></a>Vea también

[Conceptos](../windows/attributed-programming-concepts.md)