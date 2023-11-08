# Tessdata Download Buildpack

This buildpack is designed to simplify the process of downloading Tesseract OCR language data files (tessdata) from a GitHub repository and setting the TESSDATA_PREFIX environment
variable accordingly. It requires a file named tesseract_languages in your project, containing the desired languages, each on a separate line.

## Usage

Create a file named tesseract_languages in the root of your project.  
Add the ISO language codes (e.g., eng for English, deu for German) to tesseract_languages, each on a new line.  
Use this buildpack in conjunction with other buildpacks in your project, or include it as part of your build process.

## Example

### tesseract_languages File

```
osd
eng
deu
```

### Integration into java gradle bootBuildImage

```kotlin
val languagesFile = layout.projectDirectory.file("src/main/resources/tesseract_languages").toString()
bindings.add("${languagesFile}:/workspace/tesseract_languages:ro")
buildpacks.add("tessdata")
```

## Buildpack Configuration

This buildpack assumes that your project is structured appropriately with the necessary dependencies for Tesseract OCR.

During the build process, this buildpack will download the specified Tesseract language data files and set the TESSDATA_PREFIX environment variable.

## Notes

The tesseract_languages file is required, and each language code should be on a separate line.
Ensure that your project has the necessary dependencies to use Tesseract OCR.
Feel free to customize this buildpack to suit your specific needs. For additional information on Tesseract OCR and language data, refer to
the [Tesseract GitHub repository](https://github.com/tesseract-ocr/tesseract).

## Licence
MIT

