# BSI Benchmark for Evaluating Background Removal in Facial Images

Background removal is the process of separating the subject from the background in a facial photograph. Technically, it requires estimating a per-pixel segmentation mask — or, more precisely, an alpha matte — that assigns each pixel to either the foreground (the head and shoulders of the subject) or the background, and that resolves the semi-transparent transition regions along hair strands and blurred edges where the two blend. The isolated subject can then be recomposited onto a uniform, plain background, as required by international standards such as ISO/IEC 39794-5 and the ICAO specifications for machine-readable travel documents, which prohibit distracting patterns, shadows, or objects behind the head. The main challenges lie in low-contrast scenarios in which the subject's hair or clothing closely matches the background in color and texture, and in avoiding artifacts such as halos, clipped hair, or color spill from the original background, all of which may degrade the quality of the facial image and, consequently, the performance of downstream face recognition.

## Call for submissions

The Federal Office for Information Security of Germany (BSI) invites developers of background removal solutions to submit their implementations.

Solutions will be evaluated under the supervision of the BSI as an independent institution. The BSI's goal is to obtain a representative and technically sound selection of current background removal algorithms that will subsequently be used for benchmarking.

## Submission

In principle, we will accept two kinds of submissions:

1. [Software-based implementations](#software-based-submission)
2. [Device-based solutions](#device-based-submission)

**DISCLAIMER:** Do not submit software-based implementations or send device-based solutions without having clarified the details. Without clarification, submissions sent to us may be ignored.

### Deadline

We accept submissions until 27 November 2026, following the process described below.

### Software-based submission

To submit your implementation:

1. Register for participation by email as described under [Registration](#registration).
2. Create a submission archive as described under [Submission archive](#submission-archive).
3. Submit your implementation by email as described under [Submission by email](#submission-by-email).

#### Registration

All communication regarding the background removal project runs through [bgr-benchmark@bsi.bund.de](mailto:bgr-benchmark@bsi.bund.de). Our public PGP key can be downloaded [here](bgr-benchmark@bsi.bund.de-pgp-public.asc); its fingerprint is `A5C8 BEDD AD74 B10D C3DA  D91A 3091 1C9E FC5E B88F`.

To register, send an email to [bgr-benchmark@bsi.bund.de](mailto:bgr-benchmark@bsi.bund.de?subject=Background%20Removal%20Registration). Sign the email with your own PGP key and be sure to attach your public PGP key. If you do not have a PGP key, you need to generate one.

After successful registration, you will receive a response from [bgr-benchmark@bsi.bund.de](mailto:bgr-benchmark@bsi.bund.de) confirming that you may submit your implementation for benchmarking.

#### Submission archive

Your submission archive must contain your implementation for background removal, which must meet the requirements described under [Specification of your implementation](#specification-of-your-implementation). 

Put everything into an archive, i.e., in tar or zip format. Then encrypt the archive for the recipient [bgr-benchmark@bsi.bund.de](mailto:bgr-benchmark@bsi.bund.de) using [our public PGP key](bgr-benchmark@bsi.bund.de-pgp-public.asc) and sign it with the PGP key you used for registration. The resulting encrypted and signed file is the submission archive.

**DISCLAIMER:** By submitting your implementation as an encrypted and signed submission archive,

- you agree that we use the submitted software for evaluation and benchmarking,
- you understand that submissions are used exclusively for evaluation purposes,
- you agree that the evaluation is conducted by our service provider secunet Security Networks AG,
- you understand that we may not consider all submissions.

**EXAMPLE:** To encrypt `submission-archive.tar` and sign it with the PGP key registered for `your.email@address.com`, run:

```bash
# Import our public key
gpg --import bgr-benchmark@bsi.bund.de-pgp-public.asc

# Verify the fingerprint of the imported key
gpg --fingerprint bgr-benchmark@bsi.bund.de

# Encrypt and sign the archive
gpg --encrypt --sign \
    --recipient bgr-benchmark@bsi.bund.de \
    --local-user your.email@address.com \
    --output submission-archive.tar.gpg \
    submission-archive.tar
```

Because our key is not certified in your web of trust, GPG will ask you to confirm that you want to use it as the recipient key (`Use this key anyway? (y/N)`). Answer `y` only after you have verified the fingerprint given above; alternatively, certify the key locally with `gpg --lsign-key bgr-benchmark@bsi.bund.de` beforehand. Send the resulting `submission-archive.tar.gpg` as your submission archive.

#### Submission by email

Once you have successfully registered and created your submission archive, use the PGP key you registered with to send a digitally signed email to [bgr-benchmark@bsi.bund.de](mailto:bgr-benchmark@bsi.bund.de?subject=Background%20Removal%20Submission) and attach the submission archive. If the archive is larger than 5 MB, do not attach it; instead, provide a URL from which we can download it.

#### Specification of your implementation

You are free to submit your implementation in the form of scripts (e.g., Python) or binaries (e.g., compiled from C/C++), but it must run on Ubuntu 24.04 or Windows 11 (both on the x86_64 architecture). Provide a README file describing which packages we need to install, how they can be installed, and how we can run your implementation.

Your implementation must accept an RGB image (PNG format) as input and produce a mask image (PNG format as well) as output. The output mask image must have the same dimensions as the input image. White pixels are considered to belong to the background, and black pixels to the subject (foreground). Pixels may be neither white nor black; such pixels are considered to belong to a region influenced by both the subject (e.g., thin hair filaments) and the background.

### Device-based submission

If you are willing to provide a device-based solution (e.g., a photo booth), contact us at [bgr-benchmark@bsi.bund.de](mailto:bgr-benchmark@bsi.bund.de?subject=Background%20Removal%20Device-Based%20Solution).

**DISCLAIMER:** Do not send device-based solutions without having clarified the details. Without clarification, submissions sent to us may be ignored.
