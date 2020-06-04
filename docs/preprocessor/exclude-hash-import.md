---
title: excluir atributo de importación
ms.date: 08/29/2019
f1_keywords:
- exclude
helpviewer_keywords:
- exclude attribute
ms.assetid: 0883248a-d4bf-420e-9848-807b28fa976e
ms.openlocfilehash: 6a3625ee0dd44f3e2731e1240fea5f3dd4ed109e
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218721"
---
# <a name="exclude-import-attribute"></a>excluir atributo de importación

**C++Cuestión**

Excluye elementos de los archivos de encabezado de la biblioteca de tipos que se generan.

## <a name="syntax"></a>Sintaxis

> **#import** *biblioteca de tipos* **Exclude (** "*nombre1*" [ **,** "*nombre2*"...] **)**

### <a name="parameters"></a>Parámetros

*Nombre1*\
Primer elemento que se excluirá.

*Nombre2*\
Opta Segundos y elementos posteriores que se van a excluir, si es necesario.

## <a name="remarks"></a>Comentarios

Las bibliotecas de tipos pueden incluir definiciones de elementos definidos en encabezados de sistema u otras bibliotecas de tipos. Este atributo puede tomar cualquier número de argumentos, donde cada es un elemento de la biblioteca de tipos de nivel superior que se va a excluir.

**Específico C++ de finalización**

## <a name="see-also"></a>Vea también

[atributos de #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import (Directiva)](../preprocessor/hash-import-directive-cpp.md)
