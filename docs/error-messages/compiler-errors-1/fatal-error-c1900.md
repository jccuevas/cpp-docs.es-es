---
title: Error irrecuperable C1900
ms.date: 11/04/2016
f1_keywords:
- C1900
helpviewer_keywords:
- C1900
ms.assetid: 3aaa583b-4c1a-45de-aa34-527d806f2cb5
ms.openlocfilehash: 6a802928315126b72397ba6e8cc61b66f46deb41
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202845"
---
# <a name="fatal-error-c1900"></a>Error irrecuperable C1900

> Error de coincidencia de Il entre '*Tool1*' versión '*número1*' y '*Tool2*' versión '*número2*'

Las herramientas ejecutadas en varias transferencias del compilador no coinciden. *número1* y *número2* hacen referencia a las fechas de los archivos. Por ejemplo, en la transferencia 1, el front-end del compilador ejecuta (c1.dll) y, en la transferencia 2, el back-end del compilador ejecuta (c2.dll). Las fechas de los archivos deben coincidir.

Para corregir este problema, asegúrese de que se han aplicado todas las actualizaciones a Visual Studio. Si el problema persiste, use **programas y características** en el panel de control de Windows para reparar o reinstalar Visual Studio.
