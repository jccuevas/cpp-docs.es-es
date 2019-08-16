---
title: Error de las herramientas del vinculador LNK1309
ms.date: 11/04/2016
f1_keywords:
- LNK1309
helpviewer_keywords:
- LNK1309
ms.assetid: 10146071-883f-4849-97d1-c7468f90efbb
ms.openlocfilehash: ea675ca835dfc3fe4881e5fabbea746a4442b10a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62187448"
---
# <a name="linker-tools-error-lnk1309"></a>Error de las herramientas del vinculador LNK1309

> *tipo1* módulo detectado; no válido con cambiar /CLRIMAGETYPE:*type2*

## <a name="remarks"></a>Comentarios

Se solicitó un tipo de imagen CLR con **/CLRIMAGETYPE** pero el vinculador no puede crear una imagen de ese tipo porque uno o varios módulos no eran compatibles con ese tipo.

Por ejemplo, verá las LNK1309 si especifica **/CLRIMAGETYPE:safe** y pasar un módulo compilado con **/CLR: pure**.

El **/CLR: pure** y **/CLR: safe** compilador opciones y compatibilidad con las bibliotecas están en desuso en Visual Studio 2015 y no se admite en Visual Studio 2017.

También verá las LNK1309 si se intenta crear una aplicación pura confianza parcial de CLR mediante .lib ptrustu [d]. Para obtener información sobre cómo crear una aplicación de confianza parcial, vea [Cómo: Crear una aplicación de confianza parcial quitando la dependencia de la biblioteca DLL de CRT](../../dotnet/create-a-partially-trusted-application.md).

Para obtener más información, consulte [/CLR (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md) y [/CLRIMAGETYPE (Especificar tipo de imagen de CLR)](../../build/reference/clrimagetype-specify-type-of-clr-image.md).