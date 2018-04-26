---
title: set_unexpected (CRT) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- set_unexpected
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- set_unexpected
dev_langs:
- C++
helpviewer_keywords:
- set_unexpected function
- unexpected function
- exception handling, termination
ms.assetid: ebcef032-4771-48e5-88aa-2a1ab8750aa6
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c740f74dc13ea22819d0f792bfc1e3dbcc9f425e
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="setunexpected-crt"></a>set_unexpected (CRT)

Instala su propia función de finalización a la que debe llamar **unexpected**.

## <a name="syntax"></a>Sintaxis

```cpp
unexpected_function set_unexpected( unexpected_function unexpFunction );
```

### <a name="parameters"></a>Parámetros

*unexpFunction*<br/>
Puntero a una función que se escribe para reemplazar la **inesperado** función.

## <a name="return-value"></a>Valor devuelto

Devuelve un puntero a la función de finalización anterior registrado por **_set_unexpected** para que la función anterior puede restaurarse más tarde. Si no se ha establecido ninguna función anterior, el valor devuelto se puede usar para restaurar el comportamiento predeterminado; puede que este valor sea NULL.

## <a name="remarks"></a>Comentarios

El **set_unexpected** función instala *unexpFunction* como la función llamada a **inesperado**. **inesperado** no se utiliza en la implementación actual de control de excepciones de C++. El **unexpected_function** tipo está definido en el controlador de eventos. H como un puntero a una función inesperado definido por el usuario, *unexpFunction* que devuelve **void**. Personalizado *unexpFunction* función no debe devolver al llamador.

```cpp
typedef void ( *unexpected_function )( );
```

De forma predeterminada, **inesperado** llamadas **finalizar**. Puede cambiar este comportamiento predeterminado escribiendo su propia función de finalización y llamando a **set_unexpected** con el nombre de la función como su argumento. **inesperado** llama a la última función especificada como argumento a **set_unexpected**.

A diferencia de la función de terminación personalizados instalada mediante una llamada a **set_terminate**, se puede producir una excepción desde *unexpFunction*.

En un entorno multiproceso, las funciones inesperadas se mantienen por separado para cada subproceso. Cada subproceso nuevo debe instalar su propia función inesperada. Por lo tanto, cada subproceso se encarga de su propio control inesperado.

En la implementación actual de Microsoft de control de excepciones de C++, **inesperado** llamadas **finalizar** de forma predeterminada y nunca llama a la biblioteca de tiempo de ejecución de control de excepciones. No hay ninguna ventaja concreta a una llamada a **inesperado** en lugar de **finalizar**.

Hay una sola **set_unexpected** controlador para vinculados dinámicamente todos los archivos DLL o exe; incluso si se llama a **set_unexpected** el controlador puede reemplazarse por otro o que se va a sustituir establecido por otro archivo DLL o EXE.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**set_unexpected**|\<eh.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Rutinas para el control de excepciones](../../c-runtime-library/exception-handling-routines.md)<br/>
[abort](abort.md)<br/>
[_get_unexpected](get-unexpected.md)<br/>
[set_terminate](set-terminate-crt.md)<br/>
[terminate](terminate-crt.md)<br/>
[unexpected](unexpected-crt.md)<br/>
