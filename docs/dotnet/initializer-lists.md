---
title: Las listas de inicializadores | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- initializer lists
ms.assetid: b3e53442-9809-4105-9226-ae845bd20cae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 981f2737d370dc25ca4e7dc6c20947b3867a0c65
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46394613"
---
# <a name="initializer-lists"></a>Listas de inicializadores

Las listas de inicializadores en los constructores se llaman ahora antes del constructor de clase base.

## <a name="remarks"></a>Comentarios

Antes de Visual C++ 2005, se llama al constructor de clase base antes de la lista de inicializadores al compilar con extensiones administradas para C++. Ahora, cuando se compila con **/CLR**, la lista de inicializadores se llama primero.

## <a name="see-also"></a>Vea también

[Cambios generales en el lenguaje (C++/CLI)](../dotnet/general-language-changes-cpp-cli.md)