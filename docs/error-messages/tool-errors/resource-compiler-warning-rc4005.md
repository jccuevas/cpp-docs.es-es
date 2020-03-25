---
title: Advertencia del compilador de recursos RC4005
ms.date: 11/04/2016
f1_keywords:
- RC4005
helpviewer_keywords:
- RC4005
ms.assetid: 71f03b4a-c9a9-415d-920f-bf2e58507f93
ms.openlocfilehash: c428fefa90cceed6a8bc9b7f6e4b95ec2db5e039
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182414"
---
# <a name="resource-compiler-warning-rc4005"></a>Advertencia del compilador de recursos RC4005

' Identifier ': nueva definición de macro

El identificador se define dos veces. El compilador usó la segunda definición de macro.

Esta advertencia puede deberse a la definición de una macro en la línea de comandos y en el código con una directiva de `#define`. También puede deberse a que se han importado macros de archivos de inclusión.

Para eliminar la advertencia, quite una de las definiciones o use una directiva de `#undef` antes de la segunda definición.
