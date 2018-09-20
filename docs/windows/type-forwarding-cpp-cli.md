---
title: Reenvío de tipos (C++ / c++ / CLI) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- type forwarding, C++
ms.assetid: ae730b69-0c27-41cc-84e1-3132783866ea
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 806003e33e60b5146bdd722fa5248011cd4939c0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46396557"
---
# <a name="type-forwarding-ccli"></a>Reenvío de tipos (C++/CLI)

*Reenvío de tipos* permite pasar un tipo de un ensamblado (ensamblado A) a otro ensamblado (ensamblado B), que no es necesario volver a compilar los clientes que utilizan el ensamblado A.

## <a name="all-platforms"></a>Todas las plataformas

Esta característica no se admite en todos los runtimes.

## <a name="windows-runtime"></a>Windows en tiempo de ejecución

Esta característica no se admite en el tiempo de ejecución de Windows.

### <a name="requirements"></a>Requisitos

Opción del compilador: `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

El ejemplo de código siguiente muestra cómo usar el reenvío de tipos.

### <a name="syntax"></a>Sintaxis

```
#using "new.dll"
[assembly:TypeForwardedTo(type::typeid)];
```

### <a name="parameters"></a>Parámetros

*new*<br/>
El ensamblado en el que va a mover la definición de tipo.

*type*<br/>
Tipo cuya definición que se va a mover a otro ensamblado.

### <a name="remarks"></a>Comentarios

Después de un componente (ensamblado) se incluye y está siendo utilizada por las aplicaciones cliente, puede usar tipo de reenvío para pasar un tipo de componente (ensamblado) a otro ensamblado, envíe el componente actualizado (y los ensamblados adicionales necesarios) y el cliente las aplicaciones seguirán funcionando sin que se están volviendo a compilar.

Reenvío de tipos solo funciona para los componentes que se hace referencia a las aplicaciones existentes. Cuando se vuelve a generar una aplicación, debe haber las referencias de ensamblado adecuado para cualquier tipo utilizado en la aplicación.

Al reenviar un tipo (A) desde un ensamblado, debe agregar el `TypeForwardedTo` atributo para ese tipo, así como una referencia de ensamblado. El ensamblado que se hace referencia debe contener uno de los siguientes:

- La definición de tipo a.

- Un `TypeForwardedTo` atributo para un tipo, así como una referencia de ensamblado.

Ejemplos de tipos que se pueden reenviar:

- clases ref

- clases de valor

- enumeraciones

- interfaces

No se puede reenviar los siguientes tipos:

- Tipos genéricos

- Tipos nativos

- Tipos anidados (si desea reenviar un tipo anidado, debe reenviar el tipo envolvente)

Puede reenviar un tipo a un ensamblado creado en cualquier lenguaje destinado a common language runtime.

Por lo tanto, si un archivo de código fuente que se usa para generar el ensamblado.dll contiene una definición de tipo (`ref class MyClass`), y desea mover ese tipo de definición de ensamblado B.dll, haría:

1. Mover el `MyClass` a un archivo de código fuente utilizado para generar B.dll la definición de tipo.

2. Compilar el ensamblado B.dll

3. Eliminar el `MyClass` escriba definición desde el código fuente que se usa para compilar A.dll y reemplácelo con lo siguiente:

    ```
    #using "B.dll"
    [assembly:TypeForwardedTo(MyClass::typeid)];
    ```

4. Compile el ensamblado A.dll.

5. Utilice A.dll sin volver a compilar las aplicaciones cliente.

### <a name="requirements"></a>Requisitos

Opción del compilador: `/clr`