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
ms.openlocfilehash: 3d3ada700955c3acd2e96aa3e8a98c25c51393c1
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43766157"
---
# <a name="c1-notation"></a>C.1 Notación
Las reglas de gramática constan del nombre de un no terminal, seguido de dos puntos, seguido de alternativas de reemplazo en líneas independientes.

El término de la expresión sintáctica<sub>opt</sub> indica que el término es opcional en el reemplazo.

La expresión sintáctica *término*<sub>optseq</sub> es equivalente a *término-seq*<sub>opt</sub> con las siguientes reglas adicionales:

*término-seq* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Término*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*término-seq* *término*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*término-seq* **,** *término*