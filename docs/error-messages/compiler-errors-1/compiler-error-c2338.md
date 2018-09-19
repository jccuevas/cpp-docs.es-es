---
title: Error del compilador C2338 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2338
dev_langs:
- C++
helpviewer_keywords:
- C2338
ms.assetid: 49bba575-1de4-4963-86c6-ce3226a2ba51
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 77bc98afdad36e0505abb58ee06ec1c7e7654ae5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46071580"
---
# <a name="compiler-error-c2338"></a>Error del compilador C2338

> *mensaje de error*

Este error puede deberse a un `static_assert` error durante la compilación. El mensaje proporcionado por el `static_assert` parámetros.

Este mensaje de error también puede generarse mediante proveedores externos al compilador. En la mayoría de los casos, estos errores notificados por un proveedor de atributos de archivo DLL, como ATLPROV. Algunas formas habituales de este mensaje se incluyen:

> '*atributo*' proveedor de atributos Atl: error ATL*número* *mensaje*

> Uso incorrecto del atributo '*atributo*'

> '*uso*': formato incorrecto para el atributo 'usage'

Estos errores suelen ser irrecuperables y pueden ir seguidos de un error irrecuperable del compilador.

Para corregir estos problemas, corrija el uso de atributos. Por ejemplo, en algunos casos, los parámetros de atributo deben declararse antes de que se pueden usar. Si se proporciona un número de error ATL, consulte la documentación de dicho error para obtener información más específica.
