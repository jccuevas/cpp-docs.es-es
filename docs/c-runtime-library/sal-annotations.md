---
title: Anotaciones de SAL
ms.date: 11/04/2016
helpviewer_keywords:
- __z annotation
- ref annotation
- _opt annotation
- __checkreturn annotatioin
- __deref_opt annotation
- deref_opt annotation
- __deref annotation
- __in annotation
- annotations [C++]
- z annotation
- _inout annotation
- __ref annotation
- full annotation
- _in annotation
- _ref annotation
- __out annotation
- _ecount annotation
- SAL annotations
- __opt annotation
- inout annotation
- in annotation
- _CA_SHOULD_CHECK_RETURN
- __bcount annotation
- _full annotation
- _bcount annotation
- deref annotation
- part annotation
- _out annotation
- __nz annotation
- __part annotation
- opt annotation
- __full annotation
- _nz annotation
- _z annotation
- out annotation
- __ecount annotation
- __inout annotation
- SAL annotations, _CA_SHOULD_CHECK_RETURN
- _deref_opt annotation
- _deref annotation
- nz annotation
- _part annotation
- ecount annotation
- bcount annotation
ms.assetid: 81893638-010c-41a0-9cb3-666fe360f3e0
ms.openlocfilehash: a50e37b41c6e90428bed5ae113d2d9f064e042d0
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57741758"
---
# <a name="sal-annotations"></a>Anotaciones de SAL

Si examina los archivos de encabezado de la biblioteca, observará algunas anotaciones inusuales, como `_In_z` y `_Out_z_cap_(_Size)`. Se trata de ejemplos del lenguaje de anotación de código fuente de Microsoft (SAL), que proporciona un conjunto de anotaciones para describir la forma en que una función usa sus parámetros; por ejemplo, las suposiciones que hace sobre ellos y lo que garantiza cuando finalice. El archivo de encabezado \<sal.h> define las anotaciones.

Para obtener más información sobre el uso de anotaciones SAL en Visual Studio, consulte [Utilizar anotaciones SAL para reducir defectos de código de C/C++](/visualstudio/code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects).

## <a name="see-also"></a>Vea también

[Características de la biblioteca CRT](../c-runtime-library/crt-library-features.md)
