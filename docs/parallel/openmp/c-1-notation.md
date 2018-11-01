---
title: C.1 Notación
ms.date: 11/04/2016
ms.assetid: a23b2631-8096-4bf3-ac23-ba4f4bd7a52a
ms.openlocfilehash: 593450b6dd7dcb30adbf8546ad96ff716c6fbc1c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50473988"
---
# <a name="c1-notation"></a>C.1 Notación

Las reglas de gramática constan del nombre de un no terminal, seguido de dos puntos, seguido de alternativas de reemplazo en líneas independientes.

El término de la expresión sintáctica<sub>opt</sub> indica que el término es opcional en el reemplazo.

La expresión sintáctica *término*<sub>optseq</sub> es equivalente a *término-seq*<sub>opt</sub> con las siguientes reglas adicionales:

*término-seq* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Término*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*término-seq* *término*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*término-seq* **,** *término*