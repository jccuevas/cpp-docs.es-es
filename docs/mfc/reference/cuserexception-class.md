---
title: CUserException (clase)
ms.date: 11/04/2016
f1_keywords:
- CUserException
helpviewer_keywords:
- operations [MFC], stopping
- exceptions [MFC], throwing
- CUserException class [MFC]
- errors [MFC], trapping
- operations [MFC]
- throwing exceptions [MFC], stopping user operations
ms.assetid: 2156ba6d-2cce-415a-9000-6f02c26fcd7d
ms.openlocfilehash: 80f64ac3f573bddc376e54f13f6c37f8c7ebc8d0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50584475"
---
# <a name="cuserexception-class"></a>CUserException (clase)

Se inicia para detener una operación de usuario final.

## <a name="syntax"></a>Sintaxis

```
class CUserException : public CSimpleException
```

## <a name="remarks"></a>Comentarios

Usar `CUserException` cuando desee usar el mecanismo de excepción throw y catch para las excepciones específicas de la aplicación. "User" en el nombre de clase puede interpretarse como "Mi usuario hizo algo excepcional que debo controlar".

Un `CUserException` normalmente se produce después de llamar a la función global `AfxMessageBox` para notificar al usuario que ha fallado una operación. Al escribir un controlador de excepciones, controlar la excepción, especialmente dado que el usuario normalmente se ya ha recibido una notificación del error. El marco de trabajo produce esta excepción en algunos casos. Para producir un `CUserException` usted mismo, alertar al usuario y, a continuación, llame a la función global `AfxThrowUserException`.

En el ejemplo siguiente, se advierte al usuario una función que contiene las operaciones que pueden producir un error y produce una `CUserException`. La función de llamada detecta la excepción y lo controla especialmente:

[!code-cpp[NVC_MFCExceptions#24](../../mfc/codesnippet/cpp/cuserexception-class_1.cpp)]

Para obtener más información sobre el uso de `CUserException`, consulte el artículo [de control de excepciones (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CUserException`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CException (clase)](../../mfc/reference/cexception-class.md)
