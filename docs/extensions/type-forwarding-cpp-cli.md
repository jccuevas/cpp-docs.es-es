---
title: Reenvío de tipos (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- type forwarding, C++
ms.assetid: ae730b69-0c27-41cc-84e1-3132783866ea
ms.openlocfilehash: 0803ecc2ffb2da2748b1ef063481aa2571f27f50
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171936"
---
# <a name="type-forwarding-ccli"></a>Reenvío de tipos (C++/CLI)

El *reenvío de tipos* le permite mover un tipo de un ensamblado (ensamblado A) a otro (ensamblado B), por lo cual no es necesario recompilar clientes que consumen el ensamblado A.

## <a name="windows-runtime"></a>Windows en tiempo de ejecución

Esta característica no se admite en Windows Runtime.

## <a name="common-language-runtime"></a>Common Language Runtime

En el ejemplo de código siguiente se muestra cómo utilizar el reenvío de tipos.

### <a name="syntax"></a>Sintaxis

```cpp
#using "new.dll"
[assembly:TypeForwardedTo(type::typeid)];
```

### <a name="parameters"></a>Parámetros

*nuevo*<br/>
Ensamblado al que mueve la definición de tipo.

*type*<br/>
Tipo cuya definición mueve a otro ensamblado.

### <a name="remarks"></a>Observaciones

Una vez que se envía un componente (ensamblado) y que las aplicaciones cliente lo usan, puede utilizar el reenvío de tipos para mover un tipo de un componente (ensamblado) a otro y enviar el componente actualizado (y cualquier ensamblado adicional necesario). Además, las aplicaciones cliente seguirán funcionando sin recompilarse.

El reenvío de tipos solo funciona para componentes a los que las aplicaciones existentes hacen referencia. Al recompilar una aplicación, las referencias de ensamblado adecuadas para los tipos usados en la aplicación deben estar presentes.

Al reenviar un tipo (tipo A) desde un ensamblado, debe agregar el atributo `TypeForwardedTo` para ese tipo, así como una referencia de ensamblado. El ensamblado al que hace referencia debe contener una de las siguientes cosas:

- Definición del tipo A.

- Un atributo `TypeForwardedTo` para el tipo A, así como una referencia de ensamblado.

Entre los ejemplos de tipos que se pueden reenviar se incluyen:

- clases de referencia

- clases de valor

- enumeraciones

- interfaces

No puede reenviar los siguientes tipos:

- Tipos genéricos

- Tipos nativos

- Tipos anidados (si desea reenviar un tipo anidado, debe reenviar el tipo envolvente)

Puede reenviar un tipo a un ensamblado creado en cualquier lenguaje que establezca Common Language Runtime como destino.

Así pues, si un archivo de código fuente usado para compilar el ensamblado A.dll contiene una definición de tipo (`ref class MyClass`) y desea moverla al ensamblado B.dell, debe hacer lo siguiente:

1. Mover la definición de tipo `MyClass` a un archivo de código fuente utilizado para compilar B.dll.

2. Compilar el ensamblado B.dll.

3. Eliminar la definición de tipo `MyClass` del código fuente utilizado para compilar A.dll y reemplazarla por lo siguiente:

    ```cpp
    #using "B.dll"
    [assembly:TypeForwardedTo(MyClass::typeid)];
    ```

4. Compilar el ensamblado A.dll.

5. Usar A.dll sin recompilar aplicaciones cliente.

### <a name="requirements"></a>Requisitos

Opción del compilador: `/clr`
