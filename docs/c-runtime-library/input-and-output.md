---
title: Entrada y salida | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- c.io
dev_langs:
- C++
helpviewer_keywords:
- input routines
- I/O [CRT]
- I/O routines
- I/O [CRT], routines
- output routines
ms.assetid: 1c177301-e341-4ca0-aedc-0a87fe1c75ae
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 09212570dec6c64687a8b8b4b30f95174c4000ff
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="input-and-output"></a>Entrada y salida

Las funciones de E/S leen datos de archivos y dispositivos y también escriben datos en ellos. Las operaciones de E/S de archivo tienen lugar en modo de texto o binario. La biblioteca en tiempo de ejecución de Microsoft tiene tres tipos de funciones de E/S:

- Las funciones de [E/S de secuencia](../c-runtime-library/stream-i-o.md) tratan los datos como una secuencia de caracteres individuales.

- Las funciones de [E/S de bajo nivel](../c-runtime-library/low-level-i-o.md) invocan el sistema operativo directamente para la operación cuyo nivel es más bajo que el que ofrecen las E/S de secuencias.

- Las funciones de [E/S de consola y puerto](../c-runtime-library/console-and-port-i-o.md) leen o escriben directamente en una consola (teclado o pantalla) o en un puerto de E/S (como un puerto de impresora).

   > [!NOTE]
   > Dado que las funciones de secuencia se almacenan en el búfer y que las funciones de bajo nivel no existen, estos dos tipos de funciones suelen ser incompatibles. Para procesar un archivo determinado, use las funciones de secuencia o de nivel bajo exclusivamente.

## <a name="see-also"></a>Vea también

[Rutinas en tiempo de ejecución Universal C por categoría](../c-runtime-library/run-time-routines-by-category.md)<br/>
