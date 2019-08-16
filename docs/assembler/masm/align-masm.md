---
title: ALIGN (MASM)
ms.date: 01/02/2019
f1_keywords:
- align
helpviewer_keywords:
- ALIGN directive
ms.assetid: 1c386b23-439f-4ec3-a6de-74427b25e47f
ms.openlocfilehash: eb42b1952b3fd59438f0dd4c29d48c91c4d8864d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62166482"
---
# <a name="align-masm"></a>ALIGN (MASM)

El **alinear** directiva alinea el siguiente elemento de datos o la instrucción en una dirección que sea un múltiplo de su parámetro. El parámetro debe ser una potencia de 2 (por ejemplo, 1, 2, 4 etc.) que es menor o igual que la alineación de segmento.

## <a name="syntax"></a>Sintaxis

> Alinear [[*número*]]

## <a name="remarks"></a>Comentarios

El **alinear** directiva le permite especificar el desplazamiento inicial de un elemento de datos o una instrucción. Datos alineados pueden mejorar el rendimiento, a costa de un espacio desaprovechado entre elementos de datos. Grandes mejoras de rendimiento pueden verse cuando se encuentran los accesos a datos en los límites que se ajusta a las líneas de la memoria caché. En los límites naturales de acceso para tipos nativos significa menos tiempo invertido en hardware interno Realineación microcódigo.

La necesidad de instrucciones alineadas es poco frecuente en los procesadores modernos que utilizan un modelo de direccionamiento sin formato, pero pueden ser necesarios para objetivos de salto en código antiguo para otros modelos de direccionamiento.

Cuando los datos están alineados, el espacio se omitió se rellena con ceros. Cuando las instrucciones están alineadas, el espacio se omitió se rellena con las instrucciones NOP de tamaño adecuado.

## <a name="see-also"></a>Vea también

[EVEN](even.md)<br/>
[Referencia de directivas](../../assembler/masm/directives-reference.md)<br/>