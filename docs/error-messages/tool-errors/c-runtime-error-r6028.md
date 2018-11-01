---
title: C Runtime Error R6028
ms.date: 11/04/2016
f1_keywords:
- R6028
helpviewer_keywords:
- R6028
ms.assetid: 81e99079-4388-4244-a4f7-4641c508871c
ms.openlocfilehash: 4992641c2456f0322b5c52eb907b159904e4c9f0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50581823"
---
# <a name="c-runtime-error-r6028"></a>C Runtime Error R6028

no puede inicializar el montón

> [!NOTE]
> Si encuentra este mensaje de error al ejecutar una aplicación, la aplicación se cerró porque tiene un problema de memoria interna. Hay muchas razones posibles para este error, pero a menudo está provocada por una condición de memoria muy bajo, un error en el programa, o por los controladores de hardware defectuoso.
>
> Puede intentar seguir estos pasos para corregir este error:
>
> - Cierre otras aplicaciones en ejecución o reinicie el equipo para liberar memoria.
> - Use la **aplicaciones y características** o **programas y características** página en el **Panel de Control** para reparar o reinstalar el programa.
> - Si la aplicación funcionaba correctamente antes de una instalación reciente de otra aplicación o controlador, utilice la **aplicaciones y características** o **programas y características** página en el **Panel de Control** para quitar el nueva aplicación o el controlador e inténtelo de nuevo la aplicación.
> - Compruebe el sitio Web de su proveedor de hardware o **Windows Update** en el **Panel de Control** para actualizaciones de software y controladores.
> - Busque una versión actualizada de la aplicación. Si el problema persiste, póngase en contacto con el proveedor de la aplicación.

**Información para programadores**

Este error aparece cuando el sistema operativo no puede crear el almacén de memoria para la aplicación. Específicamente, la biblioteca en tiempo de ejecución de C (CRT) ha llamado a la función `HeapCreate` de Win32, que ha devuelto NULL, lo que indica un error.

Si este error se produce durante el inicio de la aplicación, es posible que el sistema no pueda atender las solicitudes de montón porque se carguen controladores defectuosos. Compruebe en Windows Update o en el sitio web del distribuidor de hardware si hay controladores actualizados.