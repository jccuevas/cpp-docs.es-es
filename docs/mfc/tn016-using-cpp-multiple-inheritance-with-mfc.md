---
title: 'TN016: Usar la herencia múltiple de C++ con MFC | Microsoft Docs'
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.inheritance
dev_langs:
- C++
helpviewer_keywords:
- TN016
- MI (Multiple Inheritance)
- multiple inheritance, MFC support for
ms.assetid: 4ee27ae1-1410-43a5-b111-b6af9b84535d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4c0ed5c1bc73f58bec1f9ad0d6a790fe3d3c0239
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46444691"
---
# <a name="tn016-using-c-multiple-inheritance-with-mfc"></a>TN016: Usar la herencia múltiple de C++ con MFC

Esta nota describe cómo usar la herencia múltiple (MI) con Microsoft Foundation Classes. El uso de MI no es necesario con MFC. MI no se usa en todas las clases MFC y no es necesario para escribir una biblioteca de clases.

Las secciones siguientes describe cómo MI afecta al uso de common giros MFC, así como cubriendo algunas de las restricciones del IMF. Algunas de estas restricciones son restricciones generales de C++. Otros impuestos por la arquitectura de MFC.

Al final de esta nota técnica, encontrará una aplicación MFC completa que usa MI.

## <a name="cruntimeclass"></a>CRuntimeClass

La persistencia y los mecanismos de creación de un objeto dinámico de uso MFC la [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) estructura de datos para identificar las clases. MFC asocia a una de estas estructuras a cada clase serializable o dinámico en la aplicación. Estas estructuras se inicializan cuando se inicia la aplicación mediante el uso de un objeto estático especial de tipo `AFX_CLASSINIT`.

La implementación actual de `CRuntimeClass` no es compatible con la información de tipo en tiempo de ejecución de MI. Esto no significa que no puede usar para MI en la aplicación MFC. Sin embargo, tendrá cierta responsabilidad cuando se trabaja con objetos que tienen más de una clase base.

El [CObject:: IsKindOf](../mfc/reference/cobject-class.md#iskindof) método no determinará correctamente el tipo de un objeto, si tiene varias clases base. Por lo tanto, no puede usar [CObject](../mfc/reference/cobject-class.md) como una clase base virtual y todas las llamadas a `CObject` funciones miembro como [CObject:: Serialize](../mfc/reference/cobject-class.md#serialize) y [CObject::operator nueva](../mfc/reference/cobject-class.md#operator_new)debe tener calificadores de ámbito para que C++ puede eliminar la ambigüedad de la llamada de función correspondiente. Cuando un programa usa MI dentro de MFC, la clase que contiene el `CObject` clase base debe ser la clase más a la izquierda en la lista de clases base.

Una alternativa es usar el `dynamic_cast` operador. Convertir un objeto con MI a uno de sus clases base obligará al compilador que use las funciones en la clase base proporcionada. Para obtener más información, consulte [dynamic_cast (operador)](../cpp/dynamic-cast-operator.md).

## <a name="cobject---the-root-of-all-classes"></a>CObject - la raíz de todas las clases

Todas las clases importantes se derivan directa o indirectamente de la clase `CObject`. `CObject` Does no tiene ningún dato de miembro, pero tiene algunas funciones de forma predeterminada. Cuando se usa para MI, normalmente heredará de dos o más `CObject`-las clases derivadas. El ejemplo siguiente muestra cómo una clase puede heredar de un [CFrameWnd](../mfc/reference/cframewnd-class.md) y un [CObList](../mfc/reference/coblist-class.md):

```cpp
class CListWnd : public CFrameWnd, public CObList
{
    // ...
};
CListWnd myListWnd;
```

En este caso `CObject` se incluye dos veces. Esto significa que necesita una manera de eliminar la ambigüedad de cualquier referencia a `CObject` métodos u operadores. El **new (operador)** y [operador delete](../mfc/reference/cobject-class.md#operator_delete) son dos operadores que se deben eliminar la ambigüedad. Como otro ejemplo, el código siguiente produce un error en tiempo de compilación:

```cpp
myListWnd.Dump(afxDump); // compile time error, CFrameWnd::Dump or CObList::Dump
```

## <a name="reimplementing-cobject-methods"></a>Volver a implementar los métodos de CObject

Cuando crea una nueva clase que tiene dos o más `CObject` derivadas de las clases base, debe volver a implementar el `CObject` métodos que desea que otras personas. Operadores **nueva** y **eliminar** son obligatorios y [volcar](../mfc/reference/cobject-class.md#dump) se recomienda. El reimplements de ejemplo siguiente la **nueva** y **eliminar** operadores y `Dump` método:

```cpp
class CListWnd : public CFrameWnd, public CObList
{
public:
    void* operator new(size_t nSize)
    {
        return CFrameWnd:: operator new(nSize);
    }
    void operator delete(void* p)
    {
        CFrameWnd:: operator delete(p);
    }
    void Dump(CDumpContent& dc)
    {
        CFrameWnd::Dump(dc);
        CObList::Dump(dc);
    }
    // ...
};
```

## <a name="virtual-inheritance-of-cobject"></a>Herencia virtual de CObject

Puede parecer que heredar prácticamente `CObject` podría resolver el problema de ambigüedad de función, pero no es así. Porque no hay ningún dato de miembro en `CObject`, no es necesario herencia virtual para evitar que varias copias de una clase base de datos de miembro. En el primer ejemplo que se mostró anteriormente, el `Dump` método virtual es ambiguo aún porque se implementa de manera diferente en `CFrameWnd` y `CObList`. La mejor manera de evitar la ambigüedad es seguir las recomendaciones presentadas en la sección anterior.

## <a name="cobjectiskindof-and-run-time-typing"></a>CObject:: IsKindOf y escriba el tiempo de ejecución

El mecanismo de tipos de tiempo de ejecución compatible con MFC en `CObject` utiliza las macros DECLARE_DYNAMIC, IMPLEMENT_DYNAMIC, DECLARE_DYNCREATE, IMPLEMENT_DYNCREATE, DECLARE_SERIAL y IMPLEMENT_SERIAL. Estas macros pueden realizar una comprobación de tipo en tiempo de ejecución para garantizar la seguridad conversiones a tipo heredado.

Estas macros admiten una única clase base y funcionarán de forma limitada para las clases heredadas multiply. La clase base que especifique en IMPLEMENT_DYNAMIC o IMPLEMENT_SERIAL debe ser la clase base del primer (o más a la izquierda). Esta selección de ubicación le permitirá escribir buscando sólo la clase base de más a la izquierda. El sistema de tipos de tiempo de ejecución sepa nada acerca de las clases bases adicionales. En el ejemplo siguiente, los sistemas de tiempo de ejecución hará escriba comprobación contra `CFrameWnd`, pero sepa nada acerca de `CObList`.

```cpp
class CListWnd : public CFrameWnd, public CObList
{
    DECLARE_DYNAMIC(CListWnd)
    // ...
};
IMPLEMENT_DYNAMIC(CListWnd, CFrameWnd)
```

## <a name="cwnd-and-message-maps"></a>CWnd y mapas de mensajes

Para que el sistema de asignación de mensajes MFC para que funcione correctamente, hay dos requisitos adicionales:

- Debe haber sólo uno `CWnd`-derivado de la clase base.

- El `CWnd`-clase derivada debe ser la clase base del primer (o más a la izquierda).

Estos son algunos ejemplos que no funcionará:

```cpp
class CTwoWindows : public CFrameWnd, public CEdit
{ /* ... */ }; // error : two copies of CWnd

class CListEdit : public CObList, public CEdit
{ /* ... */ }; // error : CEdit (derived from CWnd) must be first
```

## <a name="a-sample-program-using-mi"></a>Un programa de ejemplo con MI

El ejemplo siguiente es una aplicación independiente que consta de una clase derivada de `CFrameWnd` y [CWinApp](../mfc/reference/cwinapp-class.md). No se recomienda que estructurar una aplicación de esta manera, pero este es un ejemplo de la aplicación más pequeño de MFC que tenga una clase.

```cpp
#include <afxwin.h>

class CHelloAppAndFrame : public CFrameWnd, public CWinApp
{
public:
    CHelloAppAndFrame() {}

    // Necessary because of MI disambiguity
    void* operator new(size_t nSize)
        { return CFrameWnd::operator new(nSize); }
    void operator delete(void* p)
        { CFrameWnd::operator delete(p); }

    // Implementation
    // CWinApp overrides
    virtual BOOL InitInstance();
    // CFrameWnd overrides
    virtual void PostNcDestroy();
    afx_msg void OnPaint();

    DECLARE_MESSAGE_MAP()
};

BEGIN_MESSAGE_MAP(CHelloAppAndFrame, CFrameWnd)
    ON_WM_PAINT()
END_MESSAGE_MAP()

// because the frame window is not allocated on the heap, we must
// override PostNCDestroy not to delete the frame object
void CHelloAppAndFrame::PostNcDestroy()
{
    // do nothing (do not call base class)
}

void CHelloAppAndFrame::OnPaint()
{
    CPaintDC dc(this);
    CRect rect;
    GetClientRect(rect);

    CString s = "Hello, Windows!";
    dc.SetTextAlign(TA_BASELINE | TA_CENTER);
    dc.SetTextColor(::GetSysColor(COLOR_WINDOWTEXT));
    dc.SetBkMode(TRANSPARENT);
    dc.TextOut(rect.right / 2, rect.bottom / 2, s);
}

// Application initialization
BOOL CHelloAppAndFrame::InitInstance()
{
    // first create the main frame
    if (!CFrameWnd::Create(NULL, "Multiple Inheritance Sample",
        WS_OVERLAPPEDWINDOW, rectDefault))
        return FALSE;

    // the application object is also a frame window
    m_pMainWnd = this;
    ShowWindow(m_nCmdShow);
    return TRUE;
}

CHelloAppAndFrame theHelloAppAndFrame;
```

## <a name="see-also"></a>Vea también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)
