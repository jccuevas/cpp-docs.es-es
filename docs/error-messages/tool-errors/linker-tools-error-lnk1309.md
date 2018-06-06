---
title: Las herramientas del vinculador LNK1309 Error | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1309
dev_langs:
- C++
helpviewer_keywords:
- LNK1309
ms.assetid: 10146071-883f-4849-97d1-c7468f90efbb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0ffecdc891a9fe0d1c17d6e36c87f5df10b449ec
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704103"
---
# <a name="linker-tools-error-lnk1309"></a>Error de las herramientas del vinculador LNK1309

> *tipo1* módulo detectó; no válido con conmutador/CLRIMAGETYPE:*type2*

## <a name="remarks"></a>Comentarios

Se solicitó un tipo de imagen CLR con **/CLRIMAGETYPE** pero el vinculador no puede crear una imagen de ese tipo porque uno o varios módulos no eran compatibles con ese tipo.

Por ejemplo, verá LNK1309 si especifica **/CLRIMAGETYPE:safe** y pasar un módulo compilado con **/CLR: pure**.

El **/CLR: pure** y **/CLR: safe** bibliotecas de compatibilidad con y opciones de compilador están en desuso en Visual Studio 2015 y no se admiten en Visual Studio de 2017.

También verá LNK1309 si intentan volver a compilar una aplicación pura CLR confianza parcial mediante .lib ptrustu [d]. Para obtener información sobre cómo crear una aplicación de confianza parcial, vea [Cómo: crear una aplicación de confianza parcial mediante quitando la dependencia en la DLL de biblioteca de CRT](../../dotnet/create-a-partially-trusted-application.md).

Para obtener más información, consulte [/clr (compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) y [/CLRIMAGETYPE (Especificar tipo de imagen de CLR)](../../build/reference/clrimagetype-specify-type-of-clr-image.md).