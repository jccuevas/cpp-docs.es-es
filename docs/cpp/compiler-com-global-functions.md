---
title: Funciones globales COM del compilador | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 74449d26-50a2-47c7-b175-7cf2cf83533e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cb769cf1419f7a0142a5eeae348ca432f78fb92a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46034146"
---
# <a name="compiler-com-global-functions"></a>Funciones globales COM de compilador

**Específicos de Microsoft**

Están disponibles las siguientes rutinas:

|Función|Descripción|
|--------------|-----------------|
|[_com_raise_error](../cpp/com-raise-error.md)|Se produce un [_com_error](../cpp/com-error-class.md) en respuesta a un error.|
|[_set_com_error_handler](../cpp/set-com-error-handler.md)|Reemplaza la función predeterminada que se utiliza para el control de errores de COM.|
|[ConvertBSTRToString](../cpp/convertbstrtostring.md)|Convierte un `BSTR` valor a un `char *`.|
|[ConvertStringToBSTR](../cpp/convertstringtobstr.md)|Convierte un `char *` valor a un `BSTR`.|

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Clases de compatibilidad con COM del compilador](../cpp/compiler-com-support-classes.md)<br/>
[Compatibilidad con COM del compilador](../cpp/compiler-com-support.md)