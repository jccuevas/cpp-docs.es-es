---
title: Error en tiempo de ejecución de C R6025
ms.date: 11/04/2016
f1_keywords:
- R6025
helpviewer_keywords:
- R6025
ms.assetid: afa06d98-9c36-445b-b3e7-b6409bc8e779
ms.openlocfilehash: d5edb08278b7b6b9b3eb62e92fc04410f96a8f09
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075127"
---
# <a name="c-runtime-error-r6025"></a>Error en tiempo de ejecución de C R6025

llamada de función virtual pura

> [!NOTE]
> Si encuentra este mensaje de error mientras se ejecuta una aplicación, la aplicación se cerró porque tiene un problema interno. La causa más común de este error es un error en la aplicación o una instalación dañada.
>
> Puede intentar seguir estos pasos para corregir este error:
>
> - Use la página **aplicaciones y características** o **programas y características** del **Panel de control** para reparar o reinstalar el programa.
> - Compruebe **Windows Update** en el **Panel de control** para las actualizaciones de software.
> - Busque una versión actualizada de la aplicación. Si el problema persiste, póngase en contacto con el proveedor de la aplicación.

**Información para programadores**

No se ha creado ninguna instancia de ningún objeto para controlar la llamada de función virtual pura.

Este error se produce al llamar a una función virtual en una clase base abstracta a través de un puntero que se crea mediante una conversión al tipo de la clase derivada, pero en realidad es un puntero a la clase base. Esto puede ocurrir cuando se realiza la conversión de un<strong>\*</strong> **void** a un puntero a una clase cuando se creó el<strong>\*</strong> **void** durante la construcción de la clase base.
