# srr: ww_unsystematic_rmpd errors if truth and estimate are different lengths

    Code
      ww_unsystematic_rmpd_vec(1:5, 1:4)
    Condition
      Error in `yardstick_vec()`:
      ! Length of `truth` (5) and `estimate` (4) must match.

---

    Code
      ww_unsystematic_rmpd_vec(1:4, 1:5)
    Condition
      Error in `yardstick_vec()`:
      ! Length of `truth` (4) and `estimate` (5) must match.

# srr: ww_unsystematic_rmpd errors if truth and estimate aren't numeric

    Code
      ww_unsystematic_rmpd(char_df, x, y)
    Condition
      Error in `dplyr::reframe()`:
      i In argument: `.estimate = fn(truth = .data[["x"]], estimate = .data[["y"]], na_rm = .env[["na_rm"]])`.
      Caused by error in `yardstick_vec()`:
      ! `estimate` must be numeric.

---

    Code
      ww_unsystematic_rmpd(char_df, y, x)
    Condition
      Error in `dplyr::reframe()`:
      i In argument: `.estimate = fn(truth = .data[["y"]], estimate = .data[["x"]], na_rm = .env[["na_rm"]])`.
      Caused by error in `yardstick_vec()`:
      ! `truth` must be numeric.

---

    Code
      ww_unsystematic_rmpd_vec(as.character(1:5), 1:4)
    Condition
      Error in `yardstick_vec()`:
      ! `truth` must be numeric.

---

    Code
      ww_unsystematic_rmpd_vec(1:5, as.character(1:4))
    Condition
      Error in `yardstick_vec()`:
      ! `estimate` must be numeric.

# srr: ww_unsystematic_rmpd errors if truth and estimate are list columns

    Code
      ww_unsystematic_rmpd(list_df, x, y)
    Condition
      Error in `dplyr::reframe()`:
      i In argument: `.estimate = fn(truth = .data[["x"]], estimate = .data[["y"]], na_rm = .env[["na_rm"]])`.
      Caused by error in `yardstick_vec()`:
      ! `estimate` must be numeric.

---

    Code
      ww_unsystematic_rmpd(list_df, y, x)
    Condition
      Error in `dplyr::reframe()`:
      i In argument: `.estimate = fn(truth = .data[["y"]], estimate = .data[["x"]], na_rm = .env[["na_rm"]])`.
      Caused by error in `yardstick_vec()`:
      ! `truth` must be numeric.

# srr: ww_unsystematic_rmpd removes NaN and NA when na_rm = TRUE

    Code
      round(ww_unsystematic_rmpd(missing_df, x, y)$.estimate, 15)
    Output
      [1] 0

---

    Code
      round(ww_unsystematic_rmpd(missing_df, y, x)$.estimate, 15)
    Output
      [1] 0

---

    Code
      round(ww_unsystematic_rmpd_vec(missing_df$y, missing_df$x), 15)
    Output
      [1] 0

---

    Code
      round(ww_unsystematic_rmpd_vec(missing_df$x, missing_df$y), 15)
    Output
      [1] 0

# srr: ww_unsystematic_rmpd errors on zero-length data

    Code
      ww_unsystematic_rmpd_vec(numeric(), numeric())
    Condition
      Error in `yardstick_vec()`:
      ! 0 non-missing values were passed to `truth`.

---

    Code
      ww_unsystematic_rmpd(empty_df, x, y)
    Condition
      Error in `dplyr::reframe()`:
      i In argument: `.estimate = fn(truth = .data[["x"]], estimate = .data[["y"]], na_rm = .env[["na_rm"]])`.
      Caused by error in `yardstick_vec()`:
      ! 0 non-missing values were passed to `truth`.

---

    Code
      ww_unsystematic_rmpd(empty_df, y, x)
    Condition
      Error in `dplyr::reframe()`:
      i In argument: `.estimate = fn(truth = .data[["y"]], estimate = .data[["x"]], na_rm = .env[["na_rm"]])`.
      Caused by error in `yardstick_vec()`:
      ! 0 non-missing values were passed to `truth`.

# srr: ww_unsystematic_rmpd errors on all-NA data

    Code
      ww_unsystematic_rmpd_vec(rep(NA_real_, 4), 4:1)
    Condition
      Error in `yardstick_vec()`:
      ! 0 non-missing values were passed to `truth`.

---

    Code
      ww_unsystematic_rmpd_vec(1:4, rep(NA_real_, 4))
    Condition
      Error in `yardstick_vec()`:
      ! 0 non-missing values were passed to `truth`.

---

    Code
      ww_unsystematic_rmpd(all_na, x, y)
    Condition
      Error in `dplyr::reframe()`:
      i In argument: `.estimate = fn(truth = .data[["x"]], estimate = .data[["y"]], na_rm = .env[["na_rm"]])`.
      Caused by error in `yardstick_vec()`:
      ! 0 non-missing values were passed to `truth`.

---

    Code
      ww_unsystematic_rmpd(all_na, y, x)
    Condition
      Error in `dplyr::reframe()`:
      i In argument: `.estimate = fn(truth = .data[["y"]], estimate = .data[["x"]], na_rm = .env[["na_rm"]])`.
      Caused by error in `yardstick_vec()`:
      ! 0 non-missing values were passed to `truth`.

---

    Code
      ww_unsystematic_rmpd_vec(1:4, 1:4)
    Output
      [1] 0

# srr: ww_unsystematic_rmpd works with all identical data

    Code
      ww_unsystematic_rmpd(all_identical, x, y)
    Output
      # A tibble: 1 x 3
        .metric           .estimator .estimate
        <chr>             <chr>          <dbl>
      1 unsystematic_rmpd standard           0

---

    Code
      ww_unsystematic_rmpd_vec(1:4, 1:4)
    Output
      [1] 0

---

    Code
      ww_unsystematic_rmpd(all_identical, x, y)
    Output
      # A tibble: 1 x 3
        .metric           .estimator .estimate
        <chr>             <chr>          <dbl>
      1 unsystematic_rmpd standard           0

