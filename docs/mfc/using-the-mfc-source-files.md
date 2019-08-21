---
title: Uso de los archivos de código fuente de MFC
ms.date: 08/19/2019
helpviewer_keywords:
- public members
- source files
- MFC, source files
- MFC source files
- comments, MFC
- private member access
- protected member access
- source files, MFC
ms.assetid: 3230e8fb-3b69-4ddf-9538-365ac7ea5e72
ms.openlocfilehash: ca5799da7a6ada42db20e3551b3fb7262e8990a0
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/20/2019
ms.locfileid: "69631664"
---
# <a name="using-the-mfc-source-files"></a>Uso de los archivos de código fuente de MFC

La biblioteca de Microsoft Foundation Class (MFC) proporciona código fuente completo. Los archivos de encabezado (. h) se encuentran en el directorio *\atlmfc\include* Los archivos de implementación (. cpp) se encuentran en el directorio *\atlmfc\src\mfc*

En este artículo se explican las convenciones que utiliza MFC para comentar las distintas partes de cada clase, lo que significan estos comentarios y lo que se espera encontrar en cada sección. Los asistentes de Visual Studio usan convenciones similares para las clases que crean automáticamente, y es probable que encuentre estas convenciones útiles para su propio código.

Es posible que esté familiarizado con las palabras clave **Public**, **Protected**y **Private** C++ . En los archivos de encabezado de MFC, encontrará que cada clase puede tener varias de cada una de ellas. Por ejemplo, las funciones y variables de miembro público pueden estar en más de una palabra clave **Public** . Se debe a que MFC separa las variables y funciones de miembro según su uso, no por el tipo de acceso permitido. MFC utiliza de forma moderada. Incluso los elementos considerados detalles de implementación suelen estar **protegidos**y muchas veces son **públicas**. Aunque no se recomienda el acceso a los detalles de implementación, MFC deja de tomar la decisión.

En los archivos de código fuente de MFC y en los archivos de encabezado creados por el Asistente para aplicaciones MFC, encontrará comentarios como los que se incluyen en las declaraciones de clase (normalmente en este orden):

`// Constructors`

`// Attributes`

`// Operations`

`// Overridables`

`// Implementation`

## <a name="an-example-of-the-comments"></a>Un ejemplo de los comentarios

La siguiente lista parcial de clases `CStdioFile` usa la mayoría de los comentarios estándar que MFC emplea en sus clases para dividir los miembros de clase por las formas en que se usan:

```cpp
/*============================================================================*/
// STDIO file implementation

class CStdioFile : public CFile
{
    DECLARE_DYNAMIC(CStdioFile)

public:
// Constructors
    CStdioFile();

    // . . .

// Attributes
    FILE* m_pStream;    // stdio FILE
                        // m_hFile from base class is _fileno(m_pStream)

// Operations
    // reading and writing strings
    virtual void WriteString(LPCTSTR lpsz);
    virtual LPTSTR ReadString(_Out_writes_z_(nMax) LPTSTR lpsz, _In_ UINT nMax);
    virtual BOOL ReadString(CString& rString);

// Implementation
public:
    virtual ~CStdioFile();
#ifdef _DEBUG
    void Dump(CDumpContext& dc) const;
#endif
    virtual ULONGLONG GetPosition() const;
    virtual ULONGLONG GetLength() const;
    virtual BOOL Open(LPCTSTR lpszFileName, UINT nOpenFlags, CFileException* pError = NULL);

    // . . .

protected:
    void CommonBaseInit(FILE* pOpenStream, CAtlTransactionManager* pTM);
    void CommonInit(LPCTSTR lpszFileName, UINT nOpenFlags, CAtlTransactionManager* pTM);
};
```

Estos comentarios marcan de forma coherente las secciones de la declaración de clase que contienen tipos similares de miembros de clase. Tenga en cuenta que son convenciones de MFC, no reglas de conjunto.

## <a name="-constructors-comment"></a>Comentario de constructores

La `// Constructors` sección de una declaración de clase de MFC declara constructores (en C++ el sentido) y las funciones de inicialización necesarias para usar realmente el objeto. Por ejemplo, `CWnd::Create` se encuentra en la sección constructores porque antes de usar `CWnd` el objeto, se debe "crear completamente" llamando primero al C++ constructor y llamando a la `Create` función. Normalmente, estos miembros son públicos.

Por ejemplo, la `CStdioFile` clase tiene cinco constructores, uno de los cuales se muestra en la lista bajo [un ejemplo de los comentarios](#an-example-of-the-comments).

## <a name="-attributes-comment"></a>Comentario Attributes

La `// Attributes` sección de una declaración de clase de MFC contiene los atributos públicos (o propiedades) del objeto. Normalmente, los atributos son variables de miembro o funciones Get/Set. Las funciones "Get" y "SET" pueden o no ser virtuales. Las funciones "Get" suelen ser **const**, porque en la mayoría de los casos no tienen efectos secundarios. Estos miembros suelen ser públicos. Los atributos privados y protegidos se encuentran normalmente en la sección implementación.

En el ejemplo de lista de `CStdioFile`la clase, en [un ejemplo de los comentarios](#an-example-of-the-comments), la lista incluye una variable miembro, *m_pStream*. La `CDC` clase enumera casi 20 miembros en este comentario.

> [!NOTE]
> Las clases grandes, `CDC` como y `CWnd`, pueden tener tantos miembros que solo enumeran todos los atributos de un grupo no se agregaron mucho a la claridad. En tales casos, la biblioteca de clases utiliza otros comentarios como encabezados para delimitar aún más los miembros. Por ejemplo, `CDC` utiliza `// Device-Context Functions`, `// Drawing Tool Functions`, `// Drawing Attribute Functions`y más. Los grupos que representan atributos seguirán la sintaxis habitual descrita anteriormente. Muchas clases OLE tienen una sección de implementación `// Interface Maps`denominada.

## <a name="-operations-comment"></a>Comentario de operaciones

La `// Operations` sección de una declaración de clase de MFC contiene funciones miembro a las que se puede llamar en el objeto para hacer cosas o realizar acciones (realizar operaciones). Estas funciones suelen ser no**const** porque suelen tener efectos secundarios. Pueden ser virtuales o no virtuales en función de las necesidades de la clase. Normalmente, estos miembros son públicos.

En el ejemplo de lista de `CStdioFile`la clase, en [un ejemplo de los comentarios](#an-example-of-the-comments), la lista incluye tres funciones miembro bajo este `WriteString` Comentario: y dos sobrecargas de. `ReadString`

Al igual que con los atributos, las operaciones se pueden subdividir más.

## <a name="-overridables-comment"></a>Comentario reemplazables

La `// Overridables` sección de una declaración de clase de MFC contiene funciones virtuales que se pueden invalidar en una clase derivada cuando se necesita modificar el comportamiento de la clase base. Normalmente se denominan empezando por "ON", aunque no es estrictamente necesario. Las funciones están diseñadas para invalidarse y, a menudo, implementar o proporcionar algún tipo de "devolución de llamada" o "enlace". Normalmente, estos miembros están protegidos.

En el propio MFC, las funciones virtuales puras siempre se colocan en esta sección. Una función virtual pura de C++ tiene la forma:

`virtual void OnDraw( ) = 0;`

En el ejemplo de lista de `CStdioFile`la clase, en [un ejemplo de los comentarios](#an-example-of-the-comments), la lista no incluye ninguna sección reemplazables. La `CDocument`clase, por otro lado, enumera aproximadamente 10 funciones miembro que se reemplazan.

En algunas clases, también puede ver el comentario `// Advanced Overridables`. Estas funciones son aquellas que solo los programadores avanzados deben intentar reemplazar. Probablemente no necesitará invalidarlos.

> [!NOTE]
> Las convenciones descritas en este artículo también funcionan bien, en general, para las propiedades y los métodos de automatización (antes conocida como automatización OLE). Los métodos de automatización son similares a las operaciones de MFC. Las propiedades de automatización son similares a los atributos de MFC. Los eventos de automatización (admitidos para los controles ActiveX, antes conocidos como controles OLE) son similares a las funciones miembro reemplazables de MFC.

## <a name="-implementation-comment"></a>Comentario de implementación

La `// Implementation` sección es la parte más importante de cualquier declaración de clase de MFC.

En esta sección se hospedan todos los detalles de implementación. Ambas variables miembro y funciones miembro pueden aparecer en esta sección. Todo lo que se encuentra debajo de esta línea podría cambiar en una versión futura de MFC. A menos que no pueda evitarlo, no debe depender de los `// Implementation` detalles que aparecen debajo de la línea. Además, los miembros declarados debajo de la línea de implementación no están documentados, aunque se trata de una implementación en notas técnicas. Las invalidaciones de las funciones virtuales de la clase base residen en esta sección, independientemente de en qué sección se defina la función de clase base. Cuando una función invalida la implementación de la clase base, se considera un detalle de implementación. Normalmente, estos miembros están protegidos, pero no siempre.

En el `CStdioFile` listado bajo [un ejemplo de los comentarios](#an-example-of-the-comments), los miembros `// Implementation` declarados debajo del comentario se pueden declarar como **Public**, **Protected**o **Private**. Utilice estos miembros solo con precaución, ya que pueden cambiar en el futuro. Es posible que sea necesario declarar un grupo de miembros como **público** para que la implementación de la biblioteca de clases funcione correctamente. Sin embargo, no significa que pueda usar de forma segura los miembros que se declaran.

> [!NOTE]
> Puede encontrar comentarios de los tipos restantes por encima o por debajo del `// Implementation` comentario. En cualquier caso, describen los tipos de miembros que se declaran. Si aparecen debajo del `// Implementation` comentario, debe suponer que los miembros pueden cambiar en versiones futuras de MFC.

## <a name="see-also"></a>Vea también

[Temas generales de MFC](../mfc/general-mfc-topics.md)
