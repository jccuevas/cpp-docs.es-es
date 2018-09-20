---
title: C.1 notación | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a23b2631-8096-4bf3-ac23-ba4f4bd7a52a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4bbb3190dd5aa32315cd8f402f92fd94893b4b27
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46411877"
---
# <a name="c1-notation"></a>C.1 Notación

Las reglas de gramática constan del nombre de un no terminal, seguido de dos puntos, seguido de alternativas de reemplazo en líneas independientes.

El término de la expresión sintáctica<sub>opt</sub> indica que el término es opcional en el reemplazo.

La expresión sintáctica *término*<sub>optseq</sub> es equivalente a *término-seq*<sub>opt</sub> con las siguientes reglas adicionales:

*término-seq* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Término*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*término-seq* *término*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*término-seq* **,** *término*