---
title: auto_inline (Pragma)
ms.date: 08/29/2019
f1_keywords:
- auto_inline_CPP
- vc-pragma.auto_inline
helpviewer_keywords:
- pragmas, auto_inline
- auto_inline pragma
ms.assetid: f7624cd1-be76-429a-881c-65c9040acf43
ms.openlocfilehash: 59cda8cb73196215318c9570a5c067786284afaa
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216303"
---
# <a name="auto_inline-pragma"></a>auto_inline (Pragma)

Excluye las funciones definidas en el intervalo en el que se especifica **OFF** para que se considere como candidatas para la expansión automática en línea.

## <a name="syntax"></a>Sintaxis

> **#pragma auto_inline (** [{ **on** | **OFF** }] **)**

## <a name="remarks"></a>Comentarios

Para usar la Directiva pragma **auto_inline** , colóquela antes y inmediatamente después de, no dentro, una definición de función. La Directiva pragma surte efecto en cuanto se ve la primera definición de función después de la Directiva pragma.

## <a name="see-also"></a>Vea también

[Directivas pragma y la palabra clave __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
