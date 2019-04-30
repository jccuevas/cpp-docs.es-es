---
title: Error en tiempo de ejecución de C R6025
ms.date: 11/04/2016
f1_keywords:
- R6025
helpviewer_keywords:
- R6025
ms.assetid: afa06d98-9c36-445b-b3e7-b6409bc8e779
ms.openlocfilehash: 461bfb2aa46053ec56fff67de70038b1fcd97389
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62214173"
---
# <a name="c-runtime-error-r6025"></a>Error en tiempo de ejecución de C R6025

llamada de función virtual pura

> [!NOTE]
> Si encuentra este mensaje de error al ejecutar una aplicación, la aplicación se cerró porque tiene un problema interno. La razón más común de este error es un error en la aplicación o una instalación dañada.
>
> Puede intentar seguir estos pasos para corregir este error:
>
> - Use la **aplicaciones y características** o **programas y características** página en el **Panel de Control** para reparar o reinstalar el programa.
> - Comprobar **Windows Update** en el **Panel de Control** las actualizaciones de software.
> - Busque una versión actualizada de la aplicación. Si el problema persiste, póngase en contacto con el proveedor de la aplicación.

**Información para programadores**

No se ha creado una instancia de ningún objeto para controlar la llamada de función virtual pura.

Este error se debe a una llamada a una función virtual en una clase base abstracta a través de un puntero que se crea mediante una conversión al tipo de la clase derivada, pero es realmente un puntero a la clase base. Esto puede ocurrir cuando se realiza la conversión de un **void** <strong>\*</strong> a un puntero a una clase cuando la **void** <strong>\*</strong> era se creó durante la construcción de la clase base.

