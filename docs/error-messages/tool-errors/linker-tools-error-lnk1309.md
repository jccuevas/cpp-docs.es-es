---
title: Error de las herramientas del vinculador LNK1309
ms.date: 11/04/2016
f1_keywords:
- LNK1309
helpviewer_keywords:
- LNK1309
ms.assetid: 10146071-883f-4849-97d1-c7468f90efbb
ms.openlocfilehash: 88b05512fd45adb6dc96a6c130ceccb74f3ab14e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194907"
---
# <a name="linker-tools-error-lnk1309"></a>Error de las herramientas del vinculador LNK1309

> se detectó un módulo *Type1* ; no válido con el modificador/CLRIMAGETYPE:*tipo2*

## <a name="remarks"></a>Observaciones

Se solicitó un tipo de imagen de CLR con **/CLRIMAGETYPE** pero el enlazador no pudo generar una imagen de ese tipo porque uno o varios módulos no eran compatibles con ese tipo.

Por ejemplo, verá LNK1309 si especifica **/CLRIMAGETYPE: Safe** y pasa un módulo compilado con **/clr: Pure**.

Las opciones del compilador **/clr: Pure** y **/clr: Safe** y las bibliotecas de compatibilidad están en desuso en Visual Studio 2015 y no se admiten en Visual Studio 2017.

También verá LNK1309 si intenta compilar una aplicación CLR pura parcialmente confiable con ptrustu [d]. lib. Para obtener información sobre cómo crear una aplicación de confianza parcial, consulte [Cómo: crear una aplicación de confianza parcial quitando la dependencia del archivo dll de la biblioteca CRT](../../dotnet/create-a-partially-trusted-application.md).

Para obtener más información, consulte [/CLR (compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) y [/CLRIMAGETYPE (especificar tipo de imagen de CLR)](../../build/reference/clrimagetype-specify-type-of-clr-image.md).
