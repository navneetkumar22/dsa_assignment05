# PPT - DSA Assignment 05

## Answer 1:
```js
const construct2DArray = (original, m, n) => {
    if (m * n !== original.length)
        return [];
    let result = [];

    for (let i = 0; i < original.length; i += n) {
        result.push(original.slice(i, n + i));
    }

    return result;
};
```

<br/>

## Answer 2:
```js
const arrangeCoins = n => {
    let start = 0;
    let end = n + 1;

    while (start < end) {
        let mid = start + Math.floor((end - start) / 2);
        let product = ((mid + 1) * (mid + 2)) / 2;
        if (product > n) {
            end = mid;
        } else {
            start = mid + 1;
        }
    }
    return start;
};
```

<br/>

## Answer 3:
```js
const sortedSquares = nums => {
    const arr = nums.map(value => Math.pow(value, 2));
    return arr.sort((a, b) => a - b);
};
```

<br/>

## Answer 4:
```js
const findDifference = (nums1, nums2) => {
    let result = [[], []];
    nums1 = [...new Set(nums1)];
    nums2 = [...new Set(nums2)];

    for (let val of nums1) {
        if (!nums2.includes(val)) {
            result[0].push(val);
        }
    }

    for (let val of nums2) {
        if (!nums1.includes(val)) {
            result[1].push(val);
        }
    }
    return result;
};
```

<br/>

## Answer 5:
```js
const findTheDistanceValue = (arr1, arr2, d) => {
    return arr1.filter(n1 => arr2.every(n2 => Math.abs(n1 - n2) > d)).length;
};
```

<br/>

## Answer 6:
```js
const findDuplicates = nums => {
    const Obj = {};
    return nums.filter(num => {
        Obj[num] = (Obj[num] || 0) + 1;
        return Obj[num] > 1;
    })
};
```

<br/>

## Answer 7:
```js
const findMinElement = nums => {
    let low = 0;
    let high = nums.length - 1;

    while (low <= high) {
        let mid = parseInt((low + high) / 2);

        if (nums[low] == nums[mid]) {
            if (nums[low] > nums[low + 1])
                return nums[low + 1];
            else
                return nums[low];
        }

        else if (nums[high] == nums[mid]) {
            if (nums[high] > nums[high - 1])
                return nums[high - 1];
            else
                return nums[high];
        }

        else if (nums[mid] > nums[high]) {
            low = mid + 1;
        }

        else if (nums[mid] > nums[low]) {
            high = mid - 1;
        }

        else if (nums[mid] < nums[low] && nums[mid] < nums[high]) {
            high = high - 1;
        }
    }
};
```

<br/>

## Answer 8;
```js
const findOriginalArray = changed => {
    if (changed.length % 2 === 1)
        return []; // get rid of odd-length inputs
    let double = true;
    changed.sort((a, b) => a - b) // sort array in ascending order
    let i = 0;

    while (i < changed.length) {
        let pos = changed.indexOf(changed[i] * 2, i + 1); // check for presence of doubled number
        if (pos === -1) {
            double = false; // if not found, break out of the loop w/ false check
            break;
        } else {
            changed.splice(pos, 1); // if found, get rid of doubled number and move on.
            i++;
        }
    }
    return (double ? changed : []);
};
```