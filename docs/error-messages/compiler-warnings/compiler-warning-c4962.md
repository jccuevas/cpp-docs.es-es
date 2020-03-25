---
title: Advertencia del compilador C4962
ms.date: 11/04/2016
f1_keywords:
- C4962
helpviewer_keywords:
- C4962
ms.assetid: 62b156fe-04e5-4a6e-9339-6ab148185f87
ms.openlocfilehash: a600c1875040e1076978bb80c467e6232303cd82
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164851"
---
# <a name="compiler-warning-c4962"></a>Advertencia del compilador C4962

'función': se han deshabilitado las optimizaciones guiadas por perfiles porque generaban datos de perfil incoherentes

Una función no se compiló con /LTCG:PGO, porque los datos de la cuenta (perfil) para la función no son confiables. Es necesario volver a generar los perfiles para, a su vez, volver a crear el archivo .pgc que contiene los datos de perfil no confiables de esa función.

De forma predeterminada, esta advertencia está desactivada. Para obtener más información, consulte [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md).
