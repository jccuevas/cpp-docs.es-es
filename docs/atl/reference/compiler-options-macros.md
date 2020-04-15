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
ms.openlocfilehash: 702324c3300ff23bb60113529a681e3b8fa99354
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331620"
---
# <a name="compiler-options-macros"></a>Macros de opciones del compilador

Estas macros controlan características específicas del compilador.

|||
|-|-|
|[_ATL_ALL_WARNINGS](#_atl_all_warnings)|Símbolo que habilita errores en proyectos convertidos desde versiones anteriores de ATL.|
|[_ATL_APARTMENT_THREADED](#_atl_apartment_threaded)|Defina si uno o varios de los objetos utilizan el subprocesamiento de apartamento.|
|[_ATL_CSTRING_EXPLICIT_CONSTRUCTORS](#_atl_cstring_explicit_constructors)|Hace `CString` explícitos ciertos constructores, evitando cualquier conversión involuntaria.|
|[_ATL_ENABLE_PTM_WARNING](#_atl_enable_ptm_warning)|Defina esta macro para utilizar la sintaxis compatible con estándarc++, que genera el error del compilador C4867 cuando se utiliza una sintaxis no estándar para inicializar un puntero a una función miembro.|
|[_ATL_FREE_THREADED](#_atl_free_threaded)|Defina si uno o varios de los objetos utilizan subprocesos libres o neutros.|
|[_ATL_MULTI_THREADED](#_atl_multi_threaded)|Un símbolo que indica el proyecto tendrá objetos marcados como Ambos, Libre o Neutral. En su lugar, se debe utilizar [el _ATL_FREE_THREADED](#_atl_free_threaded) de macro.|
|[_ATL_NO_AUTOMATIC_NAMESPACE](#_atl_no_automatic_namespace)|Símbolo que impide el uso predeterminado del espacio de nombres como ATL.|
|[_ATL_NO_COM_SUPPORT](#_atl_no_com_support)|Símbolo que impide que el código relacionado con COM se compile con el proyecto.|
|[ATL_NO_VTABLE](#atl_no_vtable)|Símbolo que impide que el puntero vtable se inicialice en el constructor y destructor de la clase.|
|[ATL_NOINLINE](#atl_noinline)|Un símbolo que indica una función no debe insertarse.|
|[_ATL_SINGLE_THREADED](#_atl_single_threaded)|Defina si todos los objetos utilizan el modelo de roscado único.|

## <a name="_atl_all_warnings"></a><a name="_atl_all_warnings"></a>_ATL_ALL_WARNINGS

Símbolo que habilita errores en proyectos convertidos desde versiones anteriores de ATL.

```
#define _ATL_ALL_WARNINGS
```

### <a name="remarks"></a>Observaciones

Antes de Visual C++ .NET 2002, ATL deshabilitó muchas advertencias y las dejó deshabilitadas para que nunca aparecieran en el código de usuario. Concretamente:

- C4127 expresión condicional es constante

- C4786 'identificador': identificador se truncó a caracteres 'número' en la información de depuración

- C4201 extensión no estándar utilizada : estructura sin nombre / unión

- C4103 'nombre de archivo' : utilizado #pragma paquete para cambiar la alineación

- C4291 «declaración»: no se ha encontrado ninguna eliminación del operador coincidente; memoria no se liberará si la inicialización produce una excepción

- C4268 'identificador': los datos estáticos/globales 'const' inicializados con el constructor predeterminado generado por el compilador llenan el objeto con ceros

- C4702 código inalcanzable

En los proyectos convertidos desde versiones anteriores, los encabezados de bibliotecas siguen deshabilitando estas advertencias.

Al agregar la siguiente línea al archivo *pch.h* (*stdafx.h* en Visual Studio 2017 y versiones anteriores) antes de incluir encabezados de bibliotecas, este comportamiento se puede cambiar.

[!code-cpp[NVC_ATL_Utilities#97](../../atl/codesnippet/cpp/compiler-options-macros_1.h)]

Si `#define` se agrega esto, los encabezados ATL tienen cuidado de conservar el estado de estas advertencias para que no se deshabiliten globalmente (o si el usuario deshabilita explícitamente las advertencias individuales, no para habilitarlas).

Los nuevos `#define` proyectos tienen este conjunto en *pch.h* (*stdafx.h* en Visual Studio 2017 y versiones anteriores) de forma predeterminada.

## <a name="_atl_apartment_threaded"></a><a name="_atl_apartment_threaded"></a>_ATL_APARTMENT_THREADED

Defina si uno o varios de los objetos utilizan el subprocesamiento de apartamento.

```
_ATL_APARTMENT_THREADED
```

### <a name="remarks"></a>Observaciones

Especifica el subprocesamiento de apartamentos. Consulte [Especificación del modelo](../../atl/specifying-the-threading-model-for-a-project-atl.md) de subprocesos del proyecto para otras opciones de subprocesos y [Opciones, Asistente para objetos simples de ATL](../../atl/reference/options-atl-simple-object-wizard.md) para obtener una descripción de los modelos de subprocesos disponibles para un objeto ATL.

## <a name="_atl_cstring_explicit_constructors"></a><a name="_atl_cstring_explicit_constructors"></a>_ATL_CSTRING_EXPLICIT_CONSTRUCTORS

Hace `CString` explícitos ciertos constructores, evitando cualquier conversión involuntaria.

```
_ATL_CSTRING_EXPLICIT_CONSTRUCTORS
```

### <a name="remarks"></a>Observaciones

Cuando se define este constructor, todos los constructores CString que toman un único parámetro se compilan con la palabra clave explicit, lo que impide las conversiones implícitas de argumentos de entrada. Esto significa, por ejemplo, que cuando se define _UNICODE, si intenta usar una cadena char* como argumento de constructor CString, se producirá un error del compilador. Utilice esta macro en situaciones en las que necesite evitar conversiones implícitas entre tipos de cadena estrecha y ancha.

Mediante el uso de la macro _T en todos los argumentos de cadena de constructor, puede definir _ATL_CSTRING_EXPLICIT_CONSTRUCTORS y evitar errores de compilación independientemente de si _UNICODE está definido.

## <a name="_atl_enable_ptm_warning"></a><a name="_atl_enable_ptm_warning"></a>_ATL_ENABLE_PTM_WARNING

Defina esta macro para forzar el uso de la sintaxis compatible con el estándar ANSI C++ para el puntero a las funciones miembro. El uso de esta macro hará que se genere el error del compilador C4867 cuando se usa la sintaxis no estándar para inicializar un puntero a una función miembro.

```
#define _ATL_ENABLE_PTM_WARNING
```

### <a name="remarks"></a>Observaciones

Las bibliotecas ATL y MFC se han cambiado para que coincidan con el cumplimiento estándar mejorado de C++ del compilador de Microsoft C++. Según el estándar ANSI C++, la sintaxis de `&CMyClass::MyFunc`un puntero a una función miembro de clase debe ser .

Cuando no se define [_ATL_ENABLE_PTM_WARNING](#_atl_enable_ptm_warning) (el caso predeterminado), ATL/MFC deshabilita el error C4867 en las asignaciones de macros (en particular mapas de mensajes) para que el código que se creó en versiones anteriores pueda seguir buildándose como antes. Si define **_ATL_ENABLE_PTM_WARNING**, el código debe ser compatible con C++.

Sin embargo, el formulario no estándar ha quedado en desuso. Debe mover el código existente a la sintaxis compatible con c++. Por ejemplo, el código siguiente:

[!code-cpp[NVC_MFCListView#14](../../atl/reference/codesnippet/cpp/compiler-options-macros_2.cpp)]

Se debe cambiar a:

[!code-cpp[NVC_MFCListView#11](../../atl/reference/codesnippet/cpp/compiler-options-macros_3.cpp)]

Para macros de mapa, agregue el carácter de y eso y un &. No debería agregar el carácter de nuevo en el código.

## <a name="_atl_free_threaded"></a><a name="_atl_free_threaded"></a>_ATL_FREE_THREADED

Defina si uno o varios de los objetos utilizan subprocesos libres o neutros.

```
_ATL_FREE_THREADED
```

### <a name="remarks"></a>Observaciones

Especifica el subprocesamiento libre. El subprocesamiento libre equivale a un modelo de apartamento multiproceso. Consulte [Especificación del modelo](../../atl/specifying-the-threading-model-for-a-project-atl.md) de subprocesos del proyecto para otras opciones de subprocesos y [Opciones, Asistente para objetos simples de ATL](../../atl/reference/options-atl-simple-object-wizard.md) para obtener una descripción de los modelos de subprocesos disponibles para un objeto ATL.

## <a name="_atl_multi_threaded"></a><a name="_atl_multi_threaded"></a>_ATL_MULTI_THREADED

Un símbolo que indica el proyecto tendrá objetos marcados como Ambos, Libre o Neutral.

```
_ATL_MULTI_THREADED
```

### <a name="remarks"></a>Observaciones

Si se define este símbolo, ATL extraerá código que sincronizará correctamente el acceso a los datos globales. En su lugar, el nuevo código debe usar el [_ATL_FREE_THREADED](#_atl_free_threaded) de macro equivalente.

## <a name="_atl_no_automatic_namespace"></a><a name="_atl_no_automatic_namespace"></a>_ATL_NO_AUTOMATIC_NAMESPACE

Símbolo que impide el uso predeterminado del espacio de nombres como ATL.

```
_ATL_NO_AUTOMATIC_NAMESPACE
```

### <a name="remarks"></a>Observaciones

Si este símbolo no está definido, incluido atlbase.h se realizará mediante el espacio de **nombres ATL** de forma predeterminada, lo que puede dar lugar a conflictos de nomenclatura. Para evitar esto, defina este símbolo.

## <a name="_atl_no_com_support"></a><a name="_atl_no_com_support"></a>_ATL_NO_COM_SUPPORT

Símbolo que impide que el código relacionado con COM se compile con el proyecto.

```
_ATL_NO_COM_SUPPORT
```

## <a name="atl_no_vtable"></a><a name="atl_no_vtable"></a>ATL_NO_VTABLE

Símbolo que impide que el puntero vtable se inicialice en el constructor y destructor de la clase.

```
ATL_NO_VTABLE
```

### <a name="remarks"></a>Observaciones

Si se impide que el puntero vtable se inicialice en el constructor y destructor de la clase, el vinculador puede eliminar la vtable y todas las funciones a las que apunta. Se expande a **__declspec (novtable).**

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#53](../../atl/codesnippet/cpp/compiler-options-macros_4.h)]

## <a name="atl_noinline"></a><a name="atl_noinline"></a>ATL_NOINLINE

Un símbolo que indica una función no debe estar alineado.

```
    ATL_NOINLINE inline
    myfunction()
    {
    ...
    }
```

### <a name="parameters"></a>Parámetros

*myfunction*<br/>
La función que no debe insertarse.

### <a name="remarks"></a>Observaciones

Utilice este símbolo si desea asegurarse de que el compilador no inline una función, aunque debe declararse como insertada para que se pueda colocar en un archivo de encabezado. Se expande a **__declspec(noinline)**.

## <a name="_atl_single_threaded"></a><a name="_atl_single_threaded"></a>_ATL_SINGLE_THREADED

Defina si todos los objetos utilizan el modelo de roscado único

```
_ATL_SINGLE_THREADED
```

### <a name="remarks"></a>Observaciones

Especifica que el objeto siempre se ejecuta en el subproceso COM principal. Consulte [Especificación del modelo](../../atl/specifying-the-threading-model-for-a-project-atl.md) de subprocesos del proyecto para otras opciones de subprocesos y [Opciones, Asistente para objetos simples de ATL](../../atl/reference/options-atl-simple-object-wizard.md) para obtener una descripción de los modelos de subprocesos disponibles para un objeto ATL.

## <a name="see-also"></a>Consulte también

[Macros](../../atl/reference/atl-macros.md)
