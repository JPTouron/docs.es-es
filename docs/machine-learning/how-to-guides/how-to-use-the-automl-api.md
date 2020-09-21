---
title: Cómo usar la API de ML automatizada de ML.NET
description: La API de ML automatizada de ML.NET automatiza el proceso de compilación de modelos y genera un modelo listo para la implementación. Descubra las opciones que puede usar para configurar tareas de aprendizaje automático.
ms.date: 12/18/2019
ms.custom: mvc,how-to
ms.openlocfilehash: b1ef526301e01e1e75e71e0646f4d11e68215d69
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/15/2020
ms.locfileid: "90540737"
---
# <a name="how-to-use-the-mlnet-automated-machine-learning-api"></a><span data-ttu-id="c48bb-104">Cómo usar la API de aprendizaje automático automatizada de ML.NET</span><span class="sxs-lookup"><span data-stu-id="c48bb-104">How to use the ML.NET automated machine learning API</span></span>

<span data-ttu-id="c48bb-105">El aprendizaje automático automatizado (AutoML) automatiza el proceso de aplicar aprendizaje automático en los datos.</span><span class="sxs-lookup"><span data-stu-id="c48bb-105">Automated machine learning (AutoML) automates the process of applying machine learning to data.</span></span> <span data-ttu-id="c48bb-106">Dado un conjunto de datos, puede ejecutar un **experimento** de AutoML para iterar en diferentes caracterizaciones de datos, algoritmos de aprendizaje automático e hiperparámetros para seleccionar el mejor modelo.</span><span class="sxs-lookup"><span data-stu-id="c48bb-106">Given a dataset, you can run an AutoML **experiment** to iterate over different data featurizations, machine learning algorithms, and hyperparameters to select the best model.</span></span>

> [!NOTE]
> <span data-ttu-id="c48bb-107">Este tema hace referencia a la API de aprendizaje automático de ML.NET, que actualmente se encuentra en versión preliminar.</span><span class="sxs-lookup"><span data-stu-id="c48bb-107">This topic refers to the automated machine learning API for ML.NET, which is currently in preview.</span></span> <span data-ttu-id="c48bb-108">El material puede estar sujetos a cambios.</span><span class="sxs-lookup"><span data-stu-id="c48bb-108">Material may be subject to change.</span></span>

## <a name="load-data"></a><span data-ttu-id="c48bb-109">Cargar los datos</span><span class="sxs-lookup"><span data-stu-id="c48bb-109">Load data</span></span>

<span data-ttu-id="c48bb-110">El aprendizaje automático automatizado admite la carga de un conjunto de datos en un [IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="c48bb-110">Automated machine learning supports loading a dataset into an [IDataView](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="c48bb-111">Los datos pueden estar en forma de archivos de valores separados por tabulaciones (TSV) y archivos de valores separados por comas (CSV).</span><span class="sxs-lookup"><span data-stu-id="c48bb-111">Data can be in the form of tab-separated value (TSV) files and comma separated value (CSV) files.</span></span>

<span data-ttu-id="c48bb-112">Ejemplo:</span><span class="sxs-lookup"><span data-stu-id="c48bb-112">Example:</span></span>

```csharp
using Microsoft.ML;
using Microsoft.ML.AutoML;
    // ...
    MLContext mlContext = new MLContext();
    IDataView trainDataView = mlContext.Data.LoadFromTextFile<SentimentIssue>("my-data-file.csv", hasHeader: true);
```

## <a name="select-the-machine-learning-task-type"></a><span data-ttu-id="c48bb-113">Seleccionar el tipo de tarea de aprendizaje automático</span><span class="sxs-lookup"><span data-stu-id="c48bb-113">Select the machine learning task type</span></span>

<span data-ttu-id="c48bb-114">Antes de crear un experimento, determine el tipo de problema de aprendizaje automático que desea resolver.</span><span class="sxs-lookup"><span data-stu-id="c48bb-114">Before creating an experiment, determine the kind of machine learning problem you want to solve.</span></span> <span data-ttu-id="c48bb-115">El aprendizaje automático automatizado admite las siguientes tareas de ML:</span><span class="sxs-lookup"><span data-stu-id="c48bb-115">Automated machine learning supports the following ML tasks:</span></span>

* <span data-ttu-id="c48bb-116">Clasificación binaria</span><span class="sxs-lookup"><span data-stu-id="c48bb-116">Binary Classification</span></span>
* <span data-ttu-id="c48bb-117">Clasificación multiclase</span><span class="sxs-lookup"><span data-stu-id="c48bb-117">Multiclass Classification</span></span>
* <span data-ttu-id="c48bb-118">Regresión</span><span class="sxs-lookup"><span data-stu-id="c48bb-118">Regression</span></span>
* <span data-ttu-id="c48bb-119">Recomendación</span><span class="sxs-lookup"><span data-stu-id="c48bb-119">Recommendation</span></span>

## <a name="create-experiment-settings"></a><span data-ttu-id="c48bb-120">Crear una configuración de experimento</span><span class="sxs-lookup"><span data-stu-id="c48bb-120">Create experiment settings</span></span>

<span data-ttu-id="c48bb-121">Cree una configuración de experimento para el tipo de tarea de ML determinada:</span><span class="sxs-lookup"><span data-stu-id="c48bb-121">Create experiment settings for the determined ML task type:</span></span>

* <span data-ttu-id="c48bb-122">Clasificación binaria</span><span class="sxs-lookup"><span data-stu-id="c48bb-122">Binary Classification</span></span>

  ```csharp
  var experimentSettings = new BinaryExperimentSettings();
  ```

* <span data-ttu-id="c48bb-123">Clasificación multiclase</span><span class="sxs-lookup"><span data-stu-id="c48bb-123">Multiclass Classification</span></span>

  ```csharp
  var experimentSettings = new MulticlassExperimentSettings();
  ```

* <span data-ttu-id="c48bb-124">Regresión</span><span class="sxs-lookup"><span data-stu-id="c48bb-124">Regression</span></span>

  ```csharp
  var experimentSettings = new RegressionExperimentSettings();
  ```

* <span data-ttu-id="c48bb-125">Recomendación</span><span class="sxs-lookup"><span data-stu-id="c48bb-125">Recommendation</span></span>

  ```csharp
  var experimentSettings = new RecommendationExperimentSettings();
  ```

## <a name="configure-experiment-settings"></a><span data-ttu-id="c48bb-126">Establecer la configuración de experimento</span><span class="sxs-lookup"><span data-stu-id="c48bb-126">Configure experiment settings</span></span>

<span data-ttu-id="c48bb-127">Los experimentos son altamente configurables.</span><span class="sxs-lookup"><span data-stu-id="c48bb-127">Experiments are highly configurable.</span></span> <span data-ttu-id="c48bb-128">Consulte los [documentos de la API de AutoML](/dotnet/api/microsoft.ml.automl?view=ml-dotnet-preview) para obtener una lista completa de las opciones de configuración.</span><span class="sxs-lookup"><span data-stu-id="c48bb-128">See the [AutoML API docs](/dotnet/api/microsoft.ml.automl?view=ml-dotnet-preview) for a full list of configuration settings.</span></span>

<span data-ttu-id="c48bb-129">Estos son algunos ejemplos:</span><span class="sxs-lookup"><span data-stu-id="c48bb-129">Some examples include:</span></span>

1. <span data-ttu-id="c48bb-130">Especifique el tiempo máximo que se puede ejecutar el experimento.</span><span class="sxs-lookup"><span data-stu-id="c48bb-130">Specify the maximum time that the experiment is allowed to run.</span></span>

    ```csharp
    experimentSettings.MaxExperimentTimeInSeconds = 3600;
    ```

1. <span data-ttu-id="c48bb-131">Use un token de cancelación para cancelar el experimento antes de que se programe para finalizar.</span><span class="sxs-lookup"><span data-stu-id="c48bb-131">Use a cancellation token to cancel the experiment before it is scheduled to finish.</span></span>

    ```csharp
    experimentSettings.CancellationToken = cts.Token;

    // Cancel experiment after the user presses any key
    CancelExperimentAfterAnyKeyPress(cts);
    ```

1. <span data-ttu-id="c48bb-132">Especifique una métrica de optimización diferente.</span><span class="sxs-lookup"><span data-stu-id="c48bb-132">Specify a different optimizing metric.</span></span>

    ```csharp
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.OptimizingMetric = RegressionMetric.MeanSquaredError;
    ```

1. <span data-ttu-id="c48bb-133">La configuración `CacheDirectory` es un puntero a un directorio donde se guardarán todos los modelos entrenados durante la tarea de AutoML.</span><span class="sxs-lookup"><span data-stu-id="c48bb-133">The `CacheDirectory` setting is a pointer to a directory where all models trained during the AutoML task will be saved.</span></span> <span data-ttu-id="c48bb-134">Si `CacheDirectory` se establece en null, los modelos se mantendrán en memoria en lugar de que se escriban en el disco.</span><span class="sxs-lookup"><span data-stu-id="c48bb-134">If `CacheDirectory` is set to null, models will be kept in memory instead of written to disk.</span></span>

    ```csharp
    experimentSettings.CacheDirectory = null;
    ```

1. <span data-ttu-id="c48bb-135">Indique a ML automatizado que no use ciertos instructores.</span><span class="sxs-lookup"><span data-stu-id="c48bb-135">Instruct automated ML not to use certain trainers.</span></span>

    <span data-ttu-id="c48bb-136">Cada tarea explora una lista predeterminada de instructores para optimizar.</span><span class="sxs-lookup"><span data-stu-id="c48bb-136">A default list of trainers to optimize are explored per task.</span></span> <span data-ttu-id="c48bb-137">Esta lista se puede modificar para cada experimento.</span><span class="sxs-lookup"><span data-stu-id="c48bb-137">This list can be modified for each experiment.</span></span> <span data-ttu-id="c48bb-138">Por ejemplo, los instructores que se ejecutan lentamente en el conjunto de datos pueden eliminarse de la lista.</span><span class="sxs-lookup"><span data-stu-id="c48bb-138">For instance, trainers that run slowly on your dataset can be removed from the list.</span></span> <span data-ttu-id="c48bb-139">Para optimizar `experimentSettings.Trainers.Clear()` en una llamada específica de instructor, agregue el instructor que desea usar.</span><span class="sxs-lookup"><span data-stu-id="c48bb-139">To optimize on one specific trainer call `experimentSettings.Trainers.Clear()`, then add the trainer that you want to use.</span></span>

    ```csharp
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.Trainers.Remove(RegressionTrainer.LbfgsPoissonRegression);
    experimentSettings.Trainers.Remove(RegressionTrainer.OnlineGradientDescent);
    ```

<span data-ttu-id="c48bb-140">La lista de instructores admitidos por la tarea de ML se encuentra en el siguiente vínculo correspondiente:</span><span class="sxs-lookup"><span data-stu-id="c48bb-140">The list of supported trainers per ML task can be found at the corresponding link below:</span></span>

* [<span data-ttu-id="c48bb-141">Algoritmos de clasificación binaria admitidos</span><span class="sxs-lookup"><span data-stu-id="c48bb-141">Supported Binary Classification Algorithms</span></span>](xref:Microsoft.ML.AutoML.BinaryClassificationTrainer)
* [<span data-ttu-id="c48bb-142">Algoritmos de clasificación multiclase admitidos</span><span class="sxs-lookup"><span data-stu-id="c48bb-142">Supported Multiclass Classification Algorithms</span></span>](xref:Microsoft.ML.AutoML.MulticlassClassificationTrainer)
* [<span data-ttu-id="c48bb-143">Algoritmos de regresión admitidos</span><span class="sxs-lookup"><span data-stu-id="c48bb-143">Supported Regression Algorithms</span></span>](xref:Microsoft.ML.AutoML.RegressionTrainer)
* [<span data-ttu-id="c48bb-144">Algoritmos de recomendación admitidos</span><span class="sxs-lookup"><span data-stu-id="c48bb-144">Supported Recommendation Algorithms</span></span>](xref:Microsoft.ML.AutoML.RecommendationTrainer)

## <a name="optimizing-metric"></a><span data-ttu-id="c48bb-145">Métrica de optimización</span><span class="sxs-lookup"><span data-stu-id="c48bb-145">Optimizing metric</span></span>

<span data-ttu-id="c48bb-146">La métrica de optimización, tal como se muestra en el ejemplo anterior, determina la métrica que se optimizará durante el entrenamiento del modelo.</span><span class="sxs-lookup"><span data-stu-id="c48bb-146">The optimizing metric, as shown in the example above, determines the metric to be optimized during model training.</span></span> <span data-ttu-id="c48bb-147">La métrica de optimización que puede seleccionar viene determinada por el tipo de tarea que elija.</span><span class="sxs-lookup"><span data-stu-id="c48bb-147">The optimizing metric you can select is determined by the task type you choose.</span></span> <span data-ttu-id="c48bb-148">Esta es una lista de las métricas disponibles.</span><span class="sxs-lookup"><span data-stu-id="c48bb-148">Below is a list of available metrics.</span></span>

|[<span data-ttu-id="c48bb-149">Clasificación binaria</span><span class="sxs-lookup"><span data-stu-id="c48bb-149">Binary Classification</span></span>](xref:Microsoft.ML.AutoML.BinaryClassificationMetric) | [<span data-ttu-id="c48bb-150">Clasificación multiclase</span><span class="sxs-lookup"><span data-stu-id="c48bb-150">Multiclass Classification</span></span>](xref:Microsoft.ML.AutoML.MulticlassClassificationMetric) |[<span data-ttu-id="c48bb-151">Regresión y recomendación</span><span class="sxs-lookup"><span data-stu-id="c48bb-151">Regression & Recommendation</span></span>](xref:Microsoft.ML.AutoML.RegressionMetric)
|-- |-- |--
|<span data-ttu-id="c48bb-152">Exactitud</span><span class="sxs-lookup"><span data-stu-id="c48bb-152">Accuracy</span></span>| <span data-ttu-id="c48bb-153">LogLoss</span><span class="sxs-lookup"><span data-stu-id="c48bb-153">LogLoss</span></span> | <span data-ttu-id="c48bb-154">RSquared</span><span class="sxs-lookup"><span data-stu-id="c48bb-154">RSquared</span></span>
|<span data-ttu-id="c48bb-155">AreaUnderPrecisionRecallCurve</span><span class="sxs-lookup"><span data-stu-id="c48bb-155">AreaUnderPrecisionRecallCurve</span></span> | <span data-ttu-id="c48bb-156">LogLossReduction</span><span class="sxs-lookup"><span data-stu-id="c48bb-156">LogLossReduction</span></span> | <span data-ttu-id="c48bb-157">MeanAbsoluteError</span><span class="sxs-lookup"><span data-stu-id="c48bb-157">MeanAbsoluteError</span></span>
|<span data-ttu-id="c48bb-158">AreaUnderRocCurve</span><span class="sxs-lookup"><span data-stu-id="c48bb-158">AreaUnderRocCurve</span></span> | <span data-ttu-id="c48bb-159">MacroAccuracy</span><span class="sxs-lookup"><span data-stu-id="c48bb-159">MacroAccuracy</span></span> | <span data-ttu-id="c48bb-160">MeanSquaredError</span><span class="sxs-lookup"><span data-stu-id="c48bb-160">MeanSquaredError</span></span>
|<span data-ttu-id="c48bb-161">F1Score</span><span class="sxs-lookup"><span data-stu-id="c48bb-161">F1Score</span></span> | <span data-ttu-id="c48bb-162">MicroAccuracy</span><span class="sxs-lookup"><span data-stu-id="c48bb-162">MicroAccuracy</span></span> | <span data-ttu-id="c48bb-163">RootMeanSquaredError</span><span class="sxs-lookup"><span data-stu-id="c48bb-163">RootMeanSquaredError</span></span>
|<span data-ttu-id="c48bb-164">NegativePrecision</span><span class="sxs-lookup"><span data-stu-id="c48bb-164">NegativePrecision</span></span> | <span data-ttu-id="c48bb-165">TopKAccuracy</span><span class="sxs-lookup"><span data-stu-id="c48bb-165">TopKAccuracy</span></span>
|<span data-ttu-id="c48bb-166">NegativeRecall</span><span class="sxs-lookup"><span data-stu-id="c48bb-166">NegativeRecall</span></span> |
|<span data-ttu-id="c48bb-167">PositivePrecision</span><span class="sxs-lookup"><span data-stu-id="c48bb-167">PositivePrecision</span></span>
|<span data-ttu-id="c48bb-168">PositiveRecall</span><span class="sxs-lookup"><span data-stu-id="c48bb-168">PositiveRecall</span></span>

## <a name="data-pre-processing-and-featurization"></a><span data-ttu-id="c48bb-169">Caracterización y procesamiento previo de datos</span><span class="sxs-lookup"><span data-stu-id="c48bb-169">Data pre-processing and featurization</span></span>

> [!NOTE]
> <span data-ttu-id="c48bb-170">La columna de características solo admitía los tipos de <xref:System.Boolean>, <xref:System.Single> y <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="c48bb-170">The feature column only supported types of <xref:System.Boolean>, <xref:System.Single>, and <xref:System.String>.</span></span>

<span data-ttu-id="c48bb-171">El procesamiento previo de datos se produce de forma predeterminada y los pasos siguientes se realizan automáticamente:</span><span class="sxs-lookup"><span data-stu-id="c48bb-171">Data pre-processing happens by default and the following steps are performed automatically for you:</span></span>

1. <span data-ttu-id="c48bb-172">Quitar características sin información útil</span><span class="sxs-lookup"><span data-stu-id="c48bb-172">Drop features with no useful information</span></span>

    <span data-ttu-id="c48bb-173">Quitar características sin información útil de los conjuntos de validación y entrenamiento.</span><span class="sxs-lookup"><span data-stu-id="c48bb-173">Drop features with no useful information from training and validation sets.</span></span> <span data-ttu-id="c48bb-174">Estas incluyen características con todos los valores ausentes, el mismo valor en todas las filas o con una cardinalidad muy alta (p. ej., hashes, identificadores o GUID).</span><span class="sxs-lookup"><span data-stu-id="c48bb-174">These include features with all values missing, same value across all rows or with extremely high cardinality (e.g., hashes, IDs or GUIDs).</span></span>

1. <span data-ttu-id="c48bb-175">Imputación e indicación del valor ausente</span><span class="sxs-lookup"><span data-stu-id="c48bb-175">Missing value indication and imputation</span></span>

    <span data-ttu-id="c48bb-176">Rellene las celdas del valor ausente con el valor predeterminado para el tipo de datos.</span><span class="sxs-lookup"><span data-stu-id="c48bb-176">Fill missing value cells with the default value for the datatype.</span></span> <span data-ttu-id="c48bb-177">Anexe las características del indicador con el mismo número de ranuras que la columna de entrada.</span><span class="sxs-lookup"><span data-stu-id="c48bb-177">Append indicator features with the same number of slots as the input column.</span></span> <span data-ttu-id="c48bb-178">El valor de las características del indicador anexado es `1` si falta el valor de la columna de entrada y, en caso contrario, `0`.</span><span class="sxs-lookup"><span data-stu-id="c48bb-178">The value in the appended indicator features is `1` if the value in the input column is missing and `0` otherwise.</span></span>

1. <span data-ttu-id="c48bb-179">Generar características adicionales</span><span class="sxs-lookup"><span data-stu-id="c48bb-179">Generate additional features</span></span>

    <span data-ttu-id="c48bb-180">Para las características de texto: Características de bolsa de palabras mediante unigramas y gramas de tres caracteres.</span><span class="sxs-lookup"><span data-stu-id="c48bb-180">For text features: Bag-of-word features using unigrams and tri-character-grams.</span></span>

    <span data-ttu-id="c48bb-181">Para características categóricas: La codificación "One-hot" para características de baja cardinalidad y la codificación de hash "One-hot" para características categóricas de alta cardinalidad.</span><span class="sxs-lookup"><span data-stu-id="c48bb-181">For categorical features: One-hot encoding for low cardinality features, and one-hot-hash encoding for high cardinality categorical features.</span></span>

1. <span data-ttu-id="c48bb-182">Transformaciones y codificaciones</span><span class="sxs-lookup"><span data-stu-id="c48bb-182">Transformations and encodings</span></span>

    <span data-ttu-id="c48bb-183">Características de texto con muy pocos valores únicos que se transforman en características categóricas.</span><span class="sxs-lookup"><span data-stu-id="c48bb-183">Text features with very few unique values transformed into categorical features.</span></span> <span data-ttu-id="c48bb-184">En función de la cardinalidad de las características categóricas, realice una codificación "One-hot" o una codificación de hash "One-hot".</span><span class="sxs-lookup"><span data-stu-id="c48bb-184">Depending on cardinality of categorical features, perform one-hot encoding or one-hot hash encoding.</span></span>

## <a name="exit-criteria"></a><span data-ttu-id="c48bb-185">Criterios de salida</span><span class="sxs-lookup"><span data-stu-id="c48bb-185">Exit criteria</span></span>

<span data-ttu-id="c48bb-186">Defina los criterios para completar la tarea:</span><span class="sxs-lookup"><span data-stu-id="c48bb-186">Define the criteria to complete your task:</span></span>

1. <span data-ttu-id="c48bb-187">Salida después de un período de tiempo: mediante `MaxExperimentTimeInSeconds` en la configuración del experimento puede definir cuántos segundos se debe seguir ejecutando una tarea.</span><span class="sxs-lookup"><span data-stu-id="c48bb-187">Exit after a length of time - Using `MaxExperimentTimeInSeconds` in your experiment settings you can define how long in seconds that an task should continue to run.</span></span>

1. <span data-ttu-id="c48bb-188">Salida con un token de cancelación: puede usar un token de cancelación que le permita cancelar la tarea antes de que se programe para finalizar.</span><span class="sxs-lookup"><span data-stu-id="c48bb-188">Exit on a cancellation token -  You can use a cancellation token that lets you cancel the task before it is scheduled to finish.</span></span>

    ```csharp
    var cts = new CancellationTokenSource();
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.MaxExperimentTimeInSeconds = 3600;
    experimentSettings.CancellationToken = cts.Token;
    ```

## <a name="create-an-experiment"></a><span data-ttu-id="c48bb-189">Crear un experimento</span><span class="sxs-lookup"><span data-stu-id="c48bb-189">Create an experiment</span></span>

<span data-ttu-id="c48bb-190">Una vez que haya configurado las opciones del experimento, está listo para crearlo.</span><span class="sxs-lookup"><span data-stu-id="c48bb-190">Once you have configured the experiment settings, you are ready to create the experiment.</span></span>

```csharp
RegressionExperiment experiment = mlContext.Auto().CreateRegressionExperiment(experimentSettings);
```

## <a name="run-the-experiment"></a><span data-ttu-id="c48bb-191">Ejecutar el experimento</span><span class="sxs-lookup"><span data-stu-id="c48bb-191">Run the experiment</span></span>

<span data-ttu-id="c48bb-192">La ejecución del experimento desencadena el procesamiento previo de los datos, la selección del algoritmo de aprendizaje y el ajuste de los hiperparámetros.</span><span class="sxs-lookup"><span data-stu-id="c48bb-192">Running the experiment triggers data pre-processing, learning algorithm selection, and hyperparameter tuning.</span></span> <span data-ttu-id="c48bb-193">AutoML seguirá generando combinaciones de caracterización, algoritmos de aprendizaje e hiperparámetros hasta que se alcance `MaxExperimentTimeInSeconds` o se termine el experimento.</span><span class="sxs-lookup"><span data-stu-id="c48bb-193">AutoML will continue to generate combinations of featurization, learning algorithms, and hyperparameters until the `MaxExperimentTimeInSeconds` is reached or the experiment is terminated.</span></span>

```csharp
ExperimentResult<RegressionMetrics> experimentResult = experiment
    .Execute(trainingDataView, LabelColumnName, progressHandler: progressHandler);
```

<span data-ttu-id="c48bb-194">Explore otras sobrecargas para `Execute()` si desea pasar datos de validación, información de columna que indique el propósito de la columna o caracterizaciones previas.</span><span class="sxs-lookup"><span data-stu-id="c48bb-194">Explore other overloads for `Execute()` if you want to pass in validation data, column information indicating the column purpose, or prefeaturizers.</span></span>

## <a name="training-modes"></a><span data-ttu-id="c48bb-195">Modelo de entrenamiento</span><span class="sxs-lookup"><span data-stu-id="c48bb-195">Training modes</span></span>

### <a name="training-dataset"></a><span data-ttu-id="c48bb-196">Conjunto de datos de entrenamiento</span><span class="sxs-lookup"><span data-stu-id="c48bb-196">Training dataset</span></span>

<span data-ttu-id="c48bb-197">AutoML proporciona un método de ejecución de experimentos sobrecargados que permite proporcionar datos de entrenamiento.</span><span class="sxs-lookup"><span data-stu-id="c48bb-197">AutoML provides an overloaded experiment execute method which allows you to provide training data.</span></span> <span data-ttu-id="c48bb-198">Internamente, ML automatizado divide los datos en divisiones de validación de entrenamiento.</span><span class="sxs-lookup"><span data-stu-id="c48bb-198">Internally, automated ML divides the data into train-validate splits.</span></span>

```csharp
experiment.Execute(trainDataView);
```

### <a name="custom-validation-dataset"></a><span data-ttu-id="c48bb-199">Conjunto de datos de validación personalizada</span><span class="sxs-lookup"><span data-stu-id="c48bb-199">Custom validation dataset</span></span>

<span data-ttu-id="c48bb-200">Use el conjunto de datos de validación personalizada si la división aleatoria no es aceptable, como suele ser el caso con los datos de serie temporal.</span><span class="sxs-lookup"><span data-stu-id="c48bb-200">Use custom validation dataset if random split is not acceptable, as is usually the case with time series data.</span></span> <span data-ttu-id="c48bb-201">Puede especificar su propio conjunto de datos de validación.</span><span class="sxs-lookup"><span data-stu-id="c48bb-201">You can specify your own validation dataset.</span></span> <span data-ttu-id="c48bb-202">El modelo se evaluará en el conjunto de datos de validación especificado, en lugar de uno o varios conjuntos de datos aleatorios.</span><span class="sxs-lookup"><span data-stu-id="c48bb-202">The model will be evaluated against the validation dataset specified instead of one or more random datasets.</span></span>

```csharp
experiment.Execute(trainDataView, validationDataView);
```

## <a name="explore-model-metrics"></a><span data-ttu-id="c48bb-203">Explorar métricas de modelo</span><span class="sxs-lookup"><span data-stu-id="c48bb-203">Explore model metrics</span></span>

<span data-ttu-id="c48bb-204">Después de cada iteración de un experimento de ML, se almacenan las métricas relacionadas con esa tarea.</span><span class="sxs-lookup"><span data-stu-id="c48bb-204">After each iteration of an ML experiment, metrics relating to that task are stored.</span></span>

<span data-ttu-id="c48bb-205">Por ejemplo, podemos acceder a las métricas de validación de la mejor ejecución:</span><span class="sxs-lookup"><span data-stu-id="c48bb-205">For example, we can access validation metrics from the best run:</span></span>

```csharp
RegressionMetrics metrics = experimentResult.BestRun.ValidationMetrics;
Console.WriteLine($"R-Squared: {metrics.RSquared:0.##}");
Console.WriteLine($"Root Mean Squared Error: {metrics.RootMeanSquaredError:0.##}");
```

<span data-ttu-id="c48bb-206">Las siguientes son todas las métricas disponibles por tarea de ML:</span><span class="sxs-lookup"><span data-stu-id="c48bb-206">The following are all the available metrics per ML task:</span></span>

* [<span data-ttu-id="c48bb-207">Métricas de clasificación binaria</span><span class="sxs-lookup"><span data-stu-id="c48bb-207">Binary classification metrics</span></span>](xref:Microsoft.ML.AutoML.BinaryClassificationMetric)
* [<span data-ttu-id="c48bb-208">Métricas de clasificación multiclase</span><span class="sxs-lookup"><span data-stu-id="c48bb-208">Multiclass classification metrics</span></span>](xref:Microsoft.ML.AutoML.MulticlassClassificationMetric)
* [<span data-ttu-id="c48bb-209">Métricas de regresión y recomendación</span><span class="sxs-lookup"><span data-stu-id="c48bb-209">Regression & recommendation metrics</span></span>](xref:Microsoft.ML.AutoML.RegressionMetric)

## <a name="see-also"></a><span data-ttu-id="c48bb-210">Vea también</span><span class="sxs-lookup"><span data-stu-id="c48bb-210">See also</span></span>

<span data-ttu-id="c48bb-211">Para ver los ejemplos de código completos y mucho más, visite el repositorio de GitHub [machinelearning-dotnet/samples](https://github.com/dotnet/machinelearning-samples/tree/master#automate-mlnet-models-generation-preview-state).</span><span class="sxs-lookup"><span data-stu-id="c48bb-211">For full code samples and more visit the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master#automate-mlnet-models-generation-preview-state) GitHub repository.</span></span>
