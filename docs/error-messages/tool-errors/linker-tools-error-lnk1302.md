---
title: Error de las herramientas del vinculador LNK1302
ms.date: 11/04/2016
f1_keywords:
- LNK1302
helpviewer_keywords:
- LNK1302
ms.assetid: aea3c753-c2c4-4249-bbc3-f2d4f0164b5e
ms.openlocfilehash: c3b1117b31db4759b385943323a581da7a58f0c4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160450"
---
# <a name="linker-tools-error-lnk1302"></a>Error de las herramientas del vinculador LNK1302

solo admite la vinculación de elementos .netmodule seguros; no se puede vincular el archivo .netmodule

Un archivo .netmodule (compilado con **/LN**) se pasó un usuario está intentando invocar la vinculación de MSIL al vinculador.  Un módulo de C++ es válido para la vinculación de MSIL si se ha compilado con **/CLR: safe**.

Para corregir este error, compile con **/CLR: safe** para habilitar la vinculación de MSIL o pasar el **/CLR** o **/CLR: pure** archivo obj al vinculador en lugar del módulo.

Para obtener más información, consulte

- [/LN (Crear un módulo MSIL)](../../build/reference/ln-create-msil-module.md)

- [Archivos .netmodule como entrada del vinculador](../../build/reference/netmodule-files-as-linker-input.md)