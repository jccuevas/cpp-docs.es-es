---
title: Macros de opciones del compilador
ms.date: 08/19/2019
f1_keywords:
- _ATL_ALL_WARNINGS
- _ATL_APARTMENT_THREADED
- '_ATL_CSTRING_EXPLICIT_CONSTRUCTORS '
- _ATL_ENABLE_PTM_WARNING
- _ATL_FREE_THREADED
- _ATL_MULTI_THREADED
- _ATL_NO_AUTOMATIC_NAMESPACE
- _ATL_NO_COM_SUPPORT
- ATL_NO_VTABLE
- ATL_NOINLINE
- _ATL_SINGLE_THREADED
helpviewer_keywords:
- compiler options, macros
ms.assetid: a869adc6-b3de-4299-b040-9ae20b45f82c
ms.openlocfilehash: 84083c696ee7bdcbb9538bf587c4aaded7a3932e
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79423211"
---
# <a name="compiler-options-macros"></a>Macros de opciones del compilador

Estas macros controlan características específicas del compilador.

|||
|-|-|
|[_ATL_ALL_WARNINGS](#_atl_all_warnings)|Símbolo que habilita errores en proyectos convertidos de versiones anteriores de ATL.|
|[_ATL_APARTMENT_THREADED](#_atl_apartment_threaded)|Defina si uno o varios de los objetos utilizan el subprocesamiento de apartamento.|
|[_ATL_CSTRING_EXPLICIT_CONSTRUCTORS](#_atl_cstring_explicit_constructors)|Hace que algunos constructores de `CString` explícitos, lo que impide las conversiones involuntarias.|
|[_ATL_ENABLE_PTM_WARNING](#_atl_enable_ptm_warning)|Defina esta macro para usar C++ la sintaxis compatible con estándar, que genera el error del compilador C4867 cuando se usa una sintaxis no estándar para inicializar un puntero a una función miembro.|
|[_ATL_FREE_THREADED](#_atl_free_threaded)|Defina si uno o varios de los objetos usan subprocesamientos libres o neutros.|
|[_ATL_MULTI_THREADED](#_atl_multi_threaded)|Un símbolo que indica que el proyecto tendrá objetos marcados como ambos, gratis o neutro. En su lugar, se debe usar la macro [_ATL_FREE_THREADED](#_atl_free_threaded) .|
|[_ATL_NO_AUTOMATIC_NAMESPACE](#_atl_no_automatic_namespace)|Símbolo que impide el uso predeterminado del espacio de nombres como ATL.|
|[_ATL_NO_COM_SUPPORT](#_atl_no_com_support)|Símbolo que impide que el código relacionado con COM se compile con el proyecto.|
|[ATL_NO_VTABLE](#atl_no_vtable)|Símbolo que impide que el puntero vtable se inicialice en el constructor y el destructor de la clase.|
|[ATL_NOINLINE](#atl_noinline)|Un símbolo que indica una función no debe estar insertado.|
|[_ATL_SINGLE_THREADED](#_atl_single_threaded)|Defina si todos los objetos utilizan el modelo de subprocesos único.|

##  <a name="_atl_all_warnings"></a>_ATL_ALL_WARNINGS

Símbolo que habilita errores en proyectos convertidos de versiones anteriores de ATL.

```
#define _ATL_ALL_WARNINGS
```

### <a name="remarks"></a>Observaciones

Antes de C++ Visual .net 2002, ATL deshabilitaba muchas advertencias y las dejaron deshabilitadas para que nunca se muestren en el código de usuario. Concretamente:

- La expresión condicional C4127 es constante

- C4786 ' Identifier ': el identificador se truncó en ' Number ' caracteres en la información de depuración

- C4201 extensión no estándar usada: struct/union sin nombre

- C4103 ' nombredearchivo ': se usó #pragma Pack para cambiar la alineación

- C4291 ' DECLARATION ': no se encontró ninguna eliminación de operador coincidente; no se liberará memoria si la inicialización produce una excepción.

- C4268 ' Identifier ': los datos estáticos/globales ' const ' inicializados con el constructor predeterminado generado por el compilador llenan el objeto con ceros

- C4702 código inaccesible

En los proyectos convertidos a partir de versiones anteriores, las advertencias siguen deshabilitadas por los encabezados de las bibliotecas.

Al agregar la siguiente línea al archivo *PCH. h* (*stdafx. h* en Visual Studio 2017 y versiones anteriores) antes de incluir los encabezados de las bibliotecas, este comportamiento se puede cambiar.

[!code-cpp[NVC_ATL_Utilities#97](../../atl/codesnippet/cpp/compiler-options-macros_1.h)]

Si se agrega este `#define`, los encabezados ATL tienen cuidado de conservar el estado de estas advertencias para que no estén deshabilitadas de forma global (o si el usuario deshabilita explícitamente las advertencias individuales, no para habilitarlas).

Los proyectos nuevos tienen esta `#define` establecida en *PCH. h* (*stdafx. h* en Visual Studio 2017 y versiones anteriores) de forma predeterminada.

##  <a name="_atl_apartment_threaded"></a>_ATL_APARTMENT_THREADED

Defina si uno o varios de los objetos utilizan el subprocesamiento de apartamento.

```
_ATL_APARTMENT_THREADED
```

### <a name="remarks"></a>Observaciones

Especifica el subprocesamiento de apartamento. Vea [especificar el modelo de subprocesos del proyecto](../../atl/specifying-the-threading-model-for-a-project-atl.md) para otras opciones de subprocesos y [Opciones, Asistente para objetos simples ATL](../../atl/reference/options-atl-simple-object-wizard.md) para obtener una descripción de los modelos de subprocesos disponibles para un objeto ATL.

##  <a name="_atl_cstring_explicit_constructors"></a>_ATL_CSTRING_EXPLICIT_CONSTRUCTORS

Hace que algunos constructores de `CString` explícitos, lo que impide las conversiones involuntarias.

```
_ATL_CSTRING_EXPLICIT_CONSTRUCTORS
```

### <a name="remarks"></a>Observaciones

Cuando se define este constructor, todos los constructores CString que toman un único parámetro se compilan con la palabra clave Explicit, lo que evita las conversiones implícitas de los argumentos de entrada. Esto significa que, por ejemplo, cuando se define _UNICODE, si intenta utilizar una cadena char * como argumento de constructor CString, se producirá un error del compilador. Use esta macro en situaciones en las que necesite evitar conversiones implícitas entre tipos de cadena estrechos y anchos.

Mediante el uso de la macro _T en todos los argumentos de cadena de constructor, puede definir _ATL_CSTRING_EXPLICIT_CONSTRUCTORS y evitar errores de compilación independientemente de si se ha definido _UNICODE.

##  <a name="_atl_enable_ptm_warning"></a>_ATL_ENABLE_PTM_WARNING

Defina esta macro para forzar el uso de la sintaxis C++ compatible con el estándar ANSI para las funciones de puntero a miembro. El uso de esta macro hará que se genere el error del compilador C4867 cuando se use la sintaxis no estándar para inicializar un puntero a una función miembro.

```
#define _ATL_ENABLE_PTM_WARNING
```

### <a name="remarks"></a>Observaciones

Las bibliotecas de ATL y MFC se han modificado para que coincidan con el C++ cumplimiento C++ normativo mejorado del compilador de Microsoft. Según el estándar ANSI C++ , se debe `&CMyClass::MyFunc`la sintaxis de un puntero a una función miembro de clase.

Cuando no se define [_ATL_ENABLE_PTM_WARNING](#_atl_enable_ptm_warning) (el caso predeterminado), ATL/MFC deshabilita el error C4867 en las asignaciones de macro (en particular, mapas de mensajes) para que el código creado en versiones anteriores pueda continuar compilando como antes. Si define **_ATL_ENABLE_PTM_WARNING**, el código debe ser C++ compatible con el estándar.

Sin embargo, el formulario no estándar está en desuso. Debe trasladar el código existente a C++ la sintaxis compatible con el estándar. Por ejemplo, el código siguiente:

[!code-cpp[NVC_MFCListView#14](../../atl/reference/codesnippet/cpp/compiler-options-macros_2.cpp)]

Se debe cambiar a:

[!code-cpp[NVC_MFCListView#11](../../atl/reference/codesnippet/cpp/compiler-options-macros_3.cpp)]

En el caso de las macros de mapa, agregue el carácter de y comercial ' & '. No debe volver a agregar el carácter en el código.

##  <a name="_atl_free_threaded"></a>_ATL_FREE_THREADED

Defina si uno o varios de los objetos usan subprocesamientos libres o neutros.

```
_ATL_FREE_THREADED
```

### <a name="remarks"></a>Observaciones

Especifica el subprocesamiento libre. El subprocesamiento libre es equivalente a un modelo de Apartamento multiproceso. Vea [especificar el modelo de subprocesos del proyecto](../../atl/specifying-the-threading-model-for-a-project-atl.md) para otras opciones de subprocesos y [Opciones, Asistente para objetos simples ATL](../../atl/reference/options-atl-simple-object-wizard.md) para obtener una descripción de los modelos de subprocesos disponibles para un objeto ATL.

##  <a name="_atl_multi_threaded"></a>_ATL_MULTI_THREADED

Un símbolo que indica que el proyecto tendrá objetos marcados como ambos, gratis o neutro.

```
_ATL_MULTI_THREADED
```

### <a name="remarks"></a>Observaciones

Si se define este símbolo, ATL incorporará código que sincronizará correctamente el acceso a los datos globales. En su lugar, el código nuevo debe usar la macro equivalente [_ATL_FREE_THREADED](#_atl_free_threaded) .

##  <a name="_atl_no_automatic_namespace"></a>_ATL_NO_AUTOMATIC_NAMESPACE

Símbolo que impide el uso predeterminado del espacio de nombres como ATL.

```
_ATL_NO_AUTOMATIC_NAMESPACE
```

### <a name="remarks"></a>Observaciones

Si no se define este símbolo, incluir ATLBase. h realizará el uso de la **ATL de espacio de nombres** de forma predeterminada, lo que puede provocar conflictos de nomenclatura. Para evitarlo, defina este símbolo.

##  <a name="_atl_no_com_support"></a>_ATL_NO_COM_SUPPORT

Símbolo que impide que el código relacionado con COM se compile con el proyecto.

```
_ATL_NO_COM_SUPPORT
```

##  <a name="atl_no_vtable"></a>ATL_NO_VTABLE

Símbolo que impide que el puntero vtable se inicialice en el constructor y el destructor de la clase.

```
ATL_NO_VTABLE
```

### <a name="remarks"></a>Observaciones

Si no se puede inicializar el puntero vtable en el constructor y el destructor de la clase, el enlazador puede eliminar el vtable y todas las funciones a las que señala. Se expande a **__declspec (novtable)** .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#53](../../atl/codesnippet/cpp/compiler-options-macros_4.h)]

##  <a name="atl_noinline"></a>ATL_NOINLINE

Un símbolo que indica que una función no debe estar insertado.

```
    ATL_NOINLINE inline
    myfunction()
    {
    ...
    }
```

### <a name="parameters"></a>Parámetros

*myFunction*<br/>
Función que no se debe insertar.

### <a name="remarks"></a>Observaciones

Use este símbolo si desea asegurarse de que el compilador no inserta una función, aunque se debe declarar como alineada para que se pueda colocar en un archivo de encabezado. Se expande a **__declspec (noinline)** .

##  <a name="_atl_single_threaded"></a>_ATL_SINGLE_THREADED

Definir si todos los objetos utilizan el modelo de subprocesos único

```
_ATL_SINGLE_THREADED
```

### <a name="remarks"></a>Observaciones

Especifica que el objeto siempre se ejecuta en el subproceso COM principal. Vea [especificar el modelo de subprocesos del proyecto](../../atl/specifying-the-threading-model-for-a-project-atl.md) para otras opciones de subprocesos y [Opciones, Asistente para objetos simples ATL](../../atl/reference/options-atl-simple-object-wizard.md) para obtener una descripción de los modelos de subprocesos disponibles para un objeto ATL.

## <a name="see-also"></a>Consulte también

[Macros](../../atl/reference/atl-macros.md)
