---
title: ADVERTENCIA del compilador (nivel 3) C4192
ms.date: 11/04/2016
f1_keywords:
- C4192
helpviewer_keywords:
- C4192
ms.assetid: ea5f91fa-8c96-4f3f-ac42-0c8a86d4e5df
ms.openlocfilehash: 38b346e0a90729bda431b9cb578a03806be1ea4c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198983"
---
# <a name="compiler-warning-level-3-c4192"></a>ADVERTENCIA del compilador (nivel 3) C4192

se excluye ' name ' automáticamente al importar la biblioteca de tipos ' Library '

Una biblioteca `#import` contiene un elemento, *nombre*, que también se define en los encabezados del sistema Win32. Debido a las limitaciones de las bibliotecas de tipos, los nombres como **IUnknown** o GUID se definen a menudo en una biblioteca de tipos, duplicando la definición de los encabezados del sistema. `#import` detectará estos elementos y rechazará su incorporación en los archivos de encabezado. TLH y. TLI.

Para invalidar este comportamiento, use `#import` atributos [no_auto_exclude](../../preprocessor/no-auto-exclude.md) e [incluya ()](../../preprocessor/include-parens.md).
