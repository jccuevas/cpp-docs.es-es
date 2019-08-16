---
title: Compilador advertencia (nivel 3) C4192
ms.date: 11/04/2016
f1_keywords:
- C4192
helpviewer_keywords:
- C4192
ms.assetid: ea5f91fa-8c96-4f3f-ac42-0c8a86d4e5df
ms.openlocfilehash: 56b27596296b87edcc6de406e7b6621d5723815d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402234"
---
# <a name="compiler-warning-level-3-c4192"></a>Compilador advertencia (nivel 3) C4192

exclusión automática durante la importación de biblioteca de tipos 'library' de 'name'

Un `#import` biblioteca contiene un elemento, *nombre*, que se define también en los encabezados de sistema de Win32. Debido a limitaciones de las bibliotecas de tipos, nombres como **IUnknown** o GUID a menudo se definen en una biblioteca de tipos, duplicando la definición de los encabezados de sistema. `#import` detectará estos elementos e incorporarlos en los archivos de encabezado .tlh y. TLI.

Para invalidar este comportamiento, use `#import` atributos [no_auto_exclude](../../preprocessor/no-auto-exclude.md) y [include()](../../preprocessor/include-parens.md).