---
title: '&lt;permiso > (comentarios de documentación de C++)'
ms.date: 11/04/2016
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C++ XML tag
- permission C++ XML tag
ms.assetid: 537ee2bc-95bd-48e4-9ce6-3420c3da87f4
ms.openlocfilehash: 764048f7bc579afa6862bdff40968588955dc307
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57826995"
---
# <a name="ltpermissiongt"></a>&lt;permission&gt;

La etiqueta \<permission> le permite documentar el acceso de un miembro. <xref:System.Security.PermissionSet> permite especificar el acceso a un miembro.

## <a name="syntax"></a>Sintaxis

```
<permission cref="member">description</permission>
```

#### <a name="parameters"></a>Parámetros

*member*<br/>
Referencia a un miembro o campo al cual se puede llamar desde el entorno de compilación actual. El compilador comprueba si el elemento de código dado existe y traduce `member` al nombre de elemento canónico en la salida XML.  Ponga el nombre entre comillas simples o dobles.

El compilador emite una advertencia si no encuentra `member`.

Para obtener información sobre cómo crear una referencia cref a un tipo genérico, vea [\<see>](see-visual-cpp.md).

*description*<br/>
Descripción del acceso al miembro.

## <a name="remarks"></a>Comentarios

Compile con [/doc](doc-process-documentation-comments-c-cpp.md) para procesar los comentarios de documentación a un archivo.

El compilador de MSVC intentará resolver referencias cref en un paso a través de los comentarios de documentación.  Por tanto, si usa las reglas de búsqueda de C++, un símbolo que no encuentra el compilador se marcará como no resuelto. Vea [\<seealso>](seealso-visual-cpp.md) para obtener más información.

## <a name="example"></a>Ejemplo

```
// xml_permission_tag.cpp
// compile with: /clr /doc /LD
// post-build command: xdcmake xml_permission_tag.dll
using namespace System;
/// Text for class TestClass.
public ref class TestClass {
   /// <permission cref="System::Security::PermissionSet">Everyone can access this method.</permission>
   void Test() {}
};
```

## <a name="see-also"></a>Vea también

[Documentación de XML](xml-documentation-visual-cpp.md)
