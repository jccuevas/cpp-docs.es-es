---
title: Ventajas del ensamblador insertado | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- assembler [C++], advantages
- inline assembly [C++], about inline assembly
- inline assembly [C++], using
ms.assetid: 94364d97-faa7-4bdf-8473-570956986c51
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 820c862b90de3fd0d91a68d5a388b77f9a30a142
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43682725"
---
# <a name="advantages-of-inline-assembly"></a>Ventajas de ensamblado alineado

**Específicos de Microsoft**

Dado que el ensamblador alineado no requiere pasos de ensamblado y vínculo independientes y de vínculo, es más aconsejable que un ensamblador independiente. El código de ensamblado alineado puede utilizar cualquier nombre de variable o de función de C que esté en el ámbito, por lo que resulta fácil integrarlo con el código C del programa. Dado que el código de ensamblado se puede combinar alineado con instrucciones de C o C++, puede realizar tareas complicadas o imposibles en C o C++.

Entre los usos de ensamblado alineado se incluyen:

- Escritura de funciones en lenguaje de ensamblado.

- Optimización de punto en secciones de código críticas en cuanto a velocidad.

- Suministro de acceso directo de hardware para los controladores de dispositivo.

- Escritura de código de prólogo y epílogo para llamadas "naked".

El ensamblado alineado es una herramienta para fines especiales. Si piensa migrar una aplicación a equipos diferentes, es probable que desee colocar código específico del equipo en un módulo independiente. Dado que el ensamblador alineado no admite todas las directivas de macro y datos de Microsoft Macro Assembler (MASM), puede que le resulte más conveniente utilizar MASM para dichos módulos.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Ensamblador insertado](../../assembler/inline/inline-assembler.md)<br/>