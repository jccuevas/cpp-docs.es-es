---
title: Las herramientas del vinculador LNK1302 Error | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1302
dev_langs:
- C++
helpviewer_keywords:
- LNK1302
ms.assetid: aea3c753-c2c4-4249-bbc3-f2d4f0164b5e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3dc85b37d58e12602c02c2207c1f38bda9344e59
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46045515"
---
# <a name="linker-tools-error-lnk1302"></a>Error de las herramientas del vinculador LNK1302

solo admite la vinculación de elementos .netmodule seguros; no se puede vincular el archivo .netmodule

Un archivo .netmodule (compilado con **/LN**) se pasó un usuario está intentando invocar la vinculación de MSIL al vinculador.  Un módulo de C++ es válido para la vinculación de MSIL si se ha compilado con **/CLR: safe**.

Para corregir este error, compile con **/CLR: safe** para habilitar la vinculación de MSIL o pasar el **/CLR** o **/CLR: pure** archivo obj al vinculador en lugar del módulo.

Para obtener más información, consulte

- [/LN (Crear un módulo MSIL)](../../build/reference/ln-create-msil-module.md)

- [Archivos .netmodule como entrada del vinculador](../../build/reference/netmodule-files-as-linker-input.md)