---
title: Ventajas e inconvenientes del método utilizado para el vínculo a CRT
ms.date: 05/06/2019
helpviewer_keywords:
- _ATL_MIN_CRT macro
ms.assetid: 49b485f7-9487-49e4-b12a-0f710b620e2b
ms.openlocfilehash: b2e504de91cea9fef6e9acb0fc851bc2cc271e97
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221271"
---
# <a name="benefits-and-tradeoffs-of-the-method-used-to-link-to-the-crt"></a>Ventajas e inconvenientes del método utilizado para el vínculo a CRT

Puede vincular el proyecto con CRT estáticamente o dinámicamente. En la tabla siguiente se describe las ventajas e inconvenientes de hora de elegir qué método usar.

|Método|Prestación|Tradeoff|
|------------|-------------|--------------|
|Vincular estáticamente a CRT<br /><br /> (**Biblioteca en tiempo de ejecución** establecido en **uniproceso**)|El archivo DLL de CRT no es necesaria en el sistema donde se ejecutará la imagen.|Unos 25 KB de código de inicio se agrega a la imagen, aumentar sustancialmente su tamaño.|
|Vincular dinámicamente a CRT<br /><br /> (**Biblioteca en tiempo de ejecución** establecido en **multiproceso**)|La imagen no requiere código de inicio de CRT, por lo que es mucho menor.|El archivo DLL de CRT deben estar en el sistema que ejecuta la imagen.|

El tema [vinculación a CRT en un proyecto ATL](../atl/linking-to-the-crt-in-your-atl-project.md) describe cómo seleccionar el modo en que se va a vincular a la biblioteca CRT.

## <a name="see-also"></a>Vea también

[Programar con ATL y código en tiempo de ejecución de C](../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[Archivos DLL y comportamiento de la biblioteca en tiempo de ejecución de Visual C++](../build/run-time-library-behavior.md)<br/>
[Características de la biblioteca CRT](../c-runtime-library/crt-library-features.md)
