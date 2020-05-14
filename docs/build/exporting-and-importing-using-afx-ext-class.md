---
title: Exportar e importar mediante AFX_EXT_CLASS
ms.date: 11/04/2016
f1_keywords:
- afx_ext_class
helpviewer_keywords:
- AFX_EXT_CLASS macro
- exporting classes [C++]
- importing DLLs [C++]
- extension DLLs [C++], exporting classes
- executable files [C++], importing classes
- exporting DLLs [C++], AFX_EXT_CLASS macro
ms.assetid: 6b72cb2b-e92e-4ecd-bcab-c335e1d1cfde
ms.openlocfilehash: 95c72f8251a8a59833483eb948709c80a69d03d7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328608"
---
# <a name="exporting-and-importing-using-afx_ext_class"></a>Exportar e importar mediante AFX_EXT_CLASS

Los [archivos DLL de extensión de MFC](extension-dlls-overview.md) usan la macro **AFX_EXT_CLASS** para exportar clases; los ejecutables que se vinculan al archivo DLL de extensión de MFC usan la macro para importar clases. Con la macro **AFX_EXT_CLASS**, los mismos archivos de encabezado que se utilizan para compilar el archivo DLL de extensión de MFC se pueden usar con los ejecutables que se vinculan a la DLL.

En el archivo de encabezado de la DLL, agregue la palabra clave **AFX_EXT_CLASS** a la declaración de la clase de esta forma:

```cpp
class AFX_EXT_CLASS CMyClass : public CDocument
{
// <body of class>
};
```

MFC define esta macro como `__declspec(dllexport)` cuando se definen los símbolos de preprocesador `_AFXDLL` y `_AFXEXT`. Pero la macro se define como `__declspec(dllimport)` cuando se define `_AFXDLL` y no se define `_AFXEXT`. Cuando se define, el símbolo de preprocesador `_AFXDLL` indica que el ejecutable de destino (un archivo DLL o una aplicación) usa la versión compartida de MFC. Cuando se definen tanto `_AFXDLL` como `_AFXEXT`, esto indica que el archivo ejecutable de destino es un archivo DLL de extensión de MFC.

Dado que `AFX_EXT_CLASS` se define como `__declspec(dllexport)` al exportar desde un archivo DLL de extensión de MFC, puede exportar clases completas sin colocar los nombres representativos de todos los símbolos de la clase en el archivo .def.

Aunque con este método puede evitar la creación de un archivo .def y todos los nombres representativos para la clase, la creación de un archivo .def es más eficaz porque los nombres se pueden exportar por ordinal. Para usar el método de exportación mediante un archivo .def, coloque el código siguiente al principio y al final del archivo de encabezado:

```cpp
#undef AFX_DATA
#define AFX_DATA AFX_EXT_DATA
// <body of your header file>
#undef AFX_DATA
#define AFX_DATA
```

> [!CAUTION]
> Tenga cuidado al exportar funciones insertadas importadas, ya que pueden crear conflictos de versiones. Una función insertada se expande en el código de la aplicación; por tanto, si después vuelve a escribir la función, no se actualiza a menos que se vuelva a compilar la propia aplicación. Normalmente, las funciones de DLL se pueden actualizar sin volver a generar las aplicaciones que las usan.

## <a name="exporting-individual-members-in-a-class"></a>Exportación de miembros individuales en una clase

En ocasiones, es posible que quiera exportar miembros individuales de una clase. Por ejemplo, si va a exportar una clase derivada de `CDialog`, es posible que solo necesite exportar el constructor y la llamada a `DoModal`. Puede usar `AFX_EXT_CLASS` en los miembros individuales que necesite exportar.

Por ejemplo:

```cpp
class CExampleDialog : public CDialog
{
public:
   AFX_EXT_CLASS CExampleDialog();
   AFX_EXT_CLASS int DoModal();
   ...
   // rest of class definition
   ...
};
```

Como ya no se exportan todos los miembros de la clase, es posible que se encuentre con un problema adicional debido al funcionamiento de las macros de MFC. Algunas de las macros de asistente de MFC declaran o definen miembros de datos. Por tanto, estos miembros de datos también se deben exportar desde el archivo DLL.

Por ejemplo, la macro `DECLARE_DYNAMIC` se define como sigue al compilar un archivo DLL de extensión de MFC:

```cpp
#define DECLARE_DYNAMIC(class_name) \
protected: \
   static CRuntimeClass* PASCAL _GetBaseClass(); \
public: \
   static AFX_DATA CRuntimeClass class##class_name; \
   virtual CRuntimeClass* GetRuntimeClass() const; \
```

La línea que comienza con `AFX_DATA` estático declara un objeto estático dentro de la clase. Para exportar esta clase correctamente y acceder a la información en tiempo de ejecución desde un archivo ejecutable de cliente, debe exportar este objeto estático. Como el objeto estático se declara con el modificador `AFX_DATA`, solo es necesario definir `AFX_DATA` para que sea `__declspec(dllexport)` al compilar el archivo DLL y definirlo como `__declspec(dllimport)` al compilar el ejecutable del cliente. Como `AFX_EXT_CLASS` ya se define de esta manera, solo tiene que volver a definir `AFX_DATA` para que sea igual que `AFX_EXT_CLASS` en la definición de la clase.

Por ejemplo:

```cpp
#undef  AFX_DATA
#define AFX_DATA AFX_EXT_CLASS

class CExampleView : public CView
{
   DECLARE_DYNAMIC()
   // ... class definition ...
};

#undef  AFX_DATA
#define AFX_DATA
```

Como MFC siempre usa el símbolo `AFX_DATA` en los elementos de datos que define dentro de sus macros, esta técnica funciona en todos estos escenarios. Por ejemplo, funciona para `DECLARE_MESSAGE_MAP`.

> [!NOTE]
> Si va a exportar toda la clase en lugar de miembros concretos de ella, los miembros de datos estáticos se exportan de forma automática.

### <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?

- [Exportación desde un archivo DLL mediante archivos .def](exporting-from-a-dll-using-def-files.md)

- [Exportación desde un archivo DLL mediante __declspec(dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Exportación de funciones de C++ para usarlas en ejecutables del lenguaje C](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Exportación de funciones de C para usarlas en ejecutables del lenguaje C o C++](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Determinación del método de exportación que se va a usar](determining-which-exporting-method-to-use.md)

- [Importación a una aplicación mediante __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

- [Inicialización de un archivo DLL](run-time-library-behavior.md#initializing-a-dll)

### <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

- [Nombres representativos](reference/decorated-names.md)

- [Importación y exportación de funciones insertadas](importing-and-exporting-inline-functions.md)

- [Importaciones mutuas](mutual-imports.md)

## <a name="see-also"></a>Vea también

[Exportación desde un archivo DLL](exporting-from-a-dll.md)
