---
title: Ventajas de la portabilidad de los juegos de caracteres
ms.date: 11/04/2016
helpviewer_keywords:
- character sets [C++], benefits
- portability [C++], character sets
ms.assetid: bd60b925-1498-4e4f-897b-4c8ce66edcf7
ms.openlocfilehash: 446d59fe62999e5be652be5efabb53fd907fcd88
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50631356"
---
# <a name="benefits-of-character-set-portability"></a>Ventajas de la portabilidad de los juegos de caracteres

Puede beneficiarse del uso de las características de portabilidad de tiempo de ejecución de C y MFC incluso aunque no piense actualmente internacionalizar su aplicación:

- Código portable hace que el código base flexible. Más adelante se puede mover fácilmente a Unicode o MBCS.

- El uso de Unicode hace que las aplicaciones para Windows más eficaz. Dado que Windows utiliza Unicode, se deben traducir cadenas no Unicode que se pasan a y desde el sistema operativo que incurre en sobrecarga.

## <a name="see-also"></a>Vea también

[Unicode y MBCS](../text/unicode-and-mbcs.md)<br/>
[Compatibilidad con Unicode](../text/support-for-unicode.md)