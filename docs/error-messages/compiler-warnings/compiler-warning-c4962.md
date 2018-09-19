---
title: Advertencia del compilador C4962 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4962
dev_langs:
- C++
helpviewer_keywords:
- C4962
ms.assetid: 62b156fe-04e5-4a6e-9339-6ab148185f87
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: caff08744497936839e1021cef8fc86e0e8aa7e5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46066263"
---
# <a name="compiler-warning-c4962"></a>Advertencia del compilador C4962

'función': se han deshabilitado las optimizaciones guiadas por perfiles porque generaban datos de perfil incoherentes

Una función no se compiló con /LTCG:PGO, porque los datos de la cuenta (perfil) para la función no son confiables. Es necesario volver a generar los perfiles para, a su vez, volver a crear el archivo .pgc que contiene los datos de perfil no confiables de esa función.

De forma predeterminada, esta advertencia está desactivada. Para obtener más información, consulte [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md).