---
title: Error de las herramientas del vinculador LNK1302
ms.date: 11/04/2016
f1_keywords:
- LNK1302
helpviewer_keywords:
- LNK1302
ms.assetid: aea3c753-c2c4-4249-bbc3-f2d4f0164b5e
ms.openlocfilehash: 8323fa234851ce3ba12083adb74d5ee0fba0ac69
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194933"
---
# <a name="linker-tools-error-lnk1302"></a>Error de las herramientas del vinculador LNK1302

solo admite la vinculación de Safe. netmodule; no se puede vincular el archivo. netmodule

Se pasó un. netmodule (compilado con **/LN**) al vinculador en un intento del usuario de invocar la vinculación de MSIL.  Un C++ módulo es válido para la vinculación de MSIL si se compila con **/clr: Safe**.

Para corregir este error, compile con **/clr: Safe** para habilitar la vinculación de MSIL o pase el archivo **/CLR** o **/clr: Pure** . obj al enlazador en lugar del módulo.

Para obtener más información, vea

- [/LN (Crear un módulo MSIL)](../../build/reference/ln-create-msil-module.md)

- [Archivos .netmodule como entrada del vinculador](../../build/reference/netmodule-files-as-linker-input.md)
