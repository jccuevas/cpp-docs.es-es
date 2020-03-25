---
title: Error del compilador C2567
ms.date: 11/04/2016
f1_keywords:
- C2567
helpviewer_keywords:
- C2567
ms.assetid: 9c140ac9-7059-47e6-9ba1-e7939c8c0dc3
ms.openlocfilehash: 921992c678c1de0b74f99f544173478ebe809b2c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177461"
---
# <a name="compiler-error-c2567"></a>Error del compilador C2567

no se pueden abrir los metadatos en ' file '; es posible que se haya eliminado o se haya cambiado el archivo

El proceso de back-end del compilador no encontró un archivo de metadatos al que se hizo referencia en el origen (con `#using`) en el mismo directorio que tenía el proceso de front-end del compilador. Vea [la directiva #using](../../preprocessor/hash-using-directive-cpp.md) para obtener más información.

C2567 podría producirse si se compila con **/c** en un equipo y, a continuación, se intenta una generación de código en tiempo de vínculo en otro equipo. Para obtener más información, vea [/LTCG (generación de código en tiempo de vínculo)](../../build/reference/ltcg-link-time-code-generation.md)).

También puede indicar que el equipo no tenía más memoria.

Para corregir este error, asegúrese de que el archivo de metadatos está en la misma ubicación de directorio para todas las fases del proceso de compilación.
