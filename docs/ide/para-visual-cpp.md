---
title: '&lt;para&gt; (Visual C++) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- <para>
- para
dev_langs:
- C++
helpviewer_keywords:
- <para> C++ XML tag
- para C++ XML tag
ms.assetid: 35f2a1b3-bc14-4f13-bcb0-c39ccbf74d59
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c36388e34b2f1e3cdc4d5664c014463c727e8369
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46385097"
---
# <a name="ltparagt-visual-c"></a>&lt;para&gt; (Visual C++)

La etiqueta \<para> se usa dentro de otra etiqueta, como [\<summary>](../ide/summary-visual-cpp.md), [\<remarks>](../ide/remarks-visual-cpp.md) o [\<returns>](../ide/returns-visual-cpp.md), y permite dar una estructura al texto.

## <a name="syntax"></a>Sintaxis

```
<para>content</para>
```

#### <a name="parameters"></a>Parámetros

*content*<br/>
El texto del párrafo.

## <a name="remarks"></a>Comentarios

Compile con [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) para procesar los comentarios de documentación a un archivo.

## <a name="example"></a>Ejemplo

Vea [\<summary>](../ide/summary-visual-cpp.md) para obtener un ejemplo del uso de \<para>.

## <a name="see-also"></a>Vea también

[Documentación de XML](../ide/xml-documentation-visual-cpp.md)