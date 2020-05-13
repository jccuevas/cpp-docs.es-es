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
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328608"
---
# <a name="exporting-and-importing-using-afx_ext_class"></a>Exportar e importar mediante AFX_EXT_CLASS

[Los archivos DLL de extensión MFC](extension-dlls-overview.md) usan la **AFX_EXT_CLASS** de macro para exportar clases; los ejecutables que se vinculan a la DLL de extensión MFC utilizan la macro para importar clases. Con la **macro AFX_EXT_CLASS,** los mismos archivos de encabezado que se usan para compilar el archivo DLL de extensión MFC se pueden usar con los ejecutables que se vinculan al archivo DLL.

En el archivo de encabezado del archivo DLL, agregue la palabra clave **AFX_EXT_CLASS** a la declaración de la clase de la siguiente manera:

```cpp
class AFX_EXT_CLASS CMyClass : public CDocument
{
// <body of class>
};
```

MFC define esta macro `__declspec(dllexport)` como cuando `_AFXDLL` se `_AFXEXT` definen los símbolos de preprocesador y se definen. Pero la macro `__declspec(dllimport)` se `_AFXDLL` define `_AFXEXT` como cuándo se define y no se define. Cuando se define, `_AFXDLL` el símbolo de preprocesador indica que el ejecutable de destino (un archivo DLL o una aplicación) utiliza la versión compartida de MFC. Cuando `_AFXDLL` se `_AFXEXT` definen y se definen, esto indica que el ejecutable de destino es un archivo DLL de extensión MFC.

Dado `AFX_EXT_CLASS` que `__declspec(dllexport)` se define como al exportar desde un archivo DLL de extensión MFC, puede exportar clases completas sin colocar los nombres representativos para todos los símbolos de esa clase en el archivo .def.

Aunque puede evitar crear un archivo .def y todos los nombres decorados para la clase con este método, crear un archivo .def es más eficaz porque los nombres se pueden exportar por ordinal. Para utilizar el método de exportación del archivo .def, coloque el siguiente código al principio y al final del archivo de encabezado:

```cpp
#undef AFX_DATA
#define AFX_DATA AFX_EXT_DATA
// <body of your header file>
#undef AFX_DATA
#define AFX_DATA
```

> [!CAUTION]
> Tenga cuidado al exportar funciones en línea, ya que pueden crear la posibilidad de conflictos de versiones. Una función en línea se expande en el código de la aplicación; por lo tanto, si más adelante vuelve a escribir la función, no se actualiza a menos que se vuelva a compilar la propia aplicación. Normalmente, las funciones DLL se pueden actualizar sin volver a generar las aplicaciones que las utilizan.

## <a name="exporting-individual-members-in-a-class"></a>Exportación de miembros individuales en una clase

A veces es posible que desee exportar miembros individuales de su clase. Por ejemplo, si va `CDialog`a exportar una clase derivada, es posible `DoModal` que solo necesite exportar el constructor y la llamada. Puede utilizar `AFX_EXT_CLASS` en los miembros individuales que necesita exportar.

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

Dado que ya no está exportando todos los miembros de la clase, puede encontrarse con un problema adicional debido a la forma en que funcionan las macros MFC. Varias de las macros auxiliares de MFC realmente declaran o definen miembros de datos. Por lo tanto, estos miembros de datos también se deben exportar desde el archivo DLL.

Por ejemplo, `DECLARE_DYNAMIC` la macro se define de la siguiente manera al compilar un archivo DLL de extensión MFC:

```cpp
#define DECLARE_DYNAMIC(class_name) \
protected: \
   static CRuntimeClass* PASCAL _GetBaseClass(); \
public: \
   static AFX_DATA CRuntimeClass class##class_name; \
   virtual CRuntimeClass* GetRuntimeClass() const; \
```

La línea que comienza `AFX_DATA` con static es declarar un objeto estático dentro de la clase. Para exportar esta clase correctamente y tener acceso a la información en tiempo de ejecución desde un ejecutable de cliente, debe exportar este objeto estático. Dado que el objeto estático `AFX_DATA`se declara con `AFX_DATA` el `__declspec(dllexport)` modificador , solo debe `__declspec(dllimport)` definir que sea al compilar el archivo DLL y definirlo como al compilar el ejecutable de cliente. Dado `AFX_EXT_CLASS` que ya está definido de esta `AFX_DATA` manera, solo `AFX_EXT_CLASS` necesita redefinir para que sea el mismo que en torno a la definición de clase.

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

Dado que MFC `AFX_DATA` siempre usa el símbolo en los elementos de datos que define dentro de sus macros, esta técnica funciona para todos estos escenarios. Por ejemplo, funciona `DECLARE_MESSAGE_MAP`para .

> [!NOTE]
> Si exporta toda la clase en lugar de los miembros seleccionados de la clase, los miembros de datos estáticos se exportan automáticamente.

### <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?

- [Exportar desde un archivo DLL mediante archivos .def](exporting-from-a-dll-using-def-files.md)

- [Exportar desde un archivo DLL mediante__declspec(dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Exportar funciones de C++ para utilizarlas en ejecutables en lenguaje C](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Exportar funciones de C para utilizarlas en ejecutables en lenguaje C o C++](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Determinar qué método de exportación utilizar](determining-which-exporting-method-to-use.md)

- [Importación a una aplicación mediante __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

- [Inicializar un archivo DLL](run-time-library-behavior.md#initializing-a-dll)

### <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

- [Nombres decorados](reference/decorated-names.md)

- [Importar y exportar funciones inline](importing-and-exporting-inline-functions.md)

- [Importaciones mutuas](mutual-imports.md)

## <a name="see-also"></a>Consulte también

[Exportar desde un archivo DLL](exporting-from-a-dll.md)
