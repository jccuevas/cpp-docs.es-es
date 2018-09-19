---
title: C Runtime Error R6025 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6025
dev_langs:
- C++
helpviewer_keywords:
- R6025
ms.assetid: afa06d98-9c36-445b-b3e7-b6409bc8e779
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c176e77a1704e3311d8c814d1c1b530b9f94f1ec
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46070059"
---
# <a name="c-runtime-error-r6025"></a>C Runtime Error R6025

llamada de función virtual pura

> [!NOTE]
>  Si encuentra este mensaje de error al ejecutar una aplicación, la aplicación se cerró porque tiene un problema interno. La razón más común de este error es un error en la aplicación o una instalación dañada.
>
>  Puede intentar seguir estos pasos para corregir este error:
>
>  -   Use la **aplicaciones y características** o **programas y características** página en el **Panel de Control** para reparar o reinstalar el programa.
> -   Comprobar **Windows Update** en el **Panel de Control** las actualizaciones de software.
> -   Busque una versión actualizada de la aplicación. Si el problema persiste, póngase en contacto con el proveedor de la aplicación.

**Información para programadores**

No se ha creado una instancia de ningún objeto para controlar la llamada de función virtual pura.

Este error se debe a una llamada a una función virtual en una clase base abstracta a través de un puntero que se crea mediante una conversión al tipo de la clase derivada, pero es realmente un puntero a la clase base. Esto puede ocurrir cuando se realiza la conversión de un **void** <strong>\*</strong> a un puntero a una clase cuando la **void** <strong>\*</strong> era se creó durante la construcción de la clase base.

