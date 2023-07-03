// Function to find the longest common substring of two strings
function longestCommonSubstring(str1, str2) {
  // Initialize a 2D matrix to store the lengths of common substrings
  const matrix = Array(str1.length + 1)
    .fill(0)
    .map(() => Array(str2.length + 1).fill(0));

  let maxLength = 0; // Length of the longest common substring
  let endIndex = 0; // End index of the longest common substring in str1

  // Fill the matrix and track the longest common substring
  for (let i = 1; i <= str1.length; i++) {
    for (let j = 1; j <= str2.length; j++) {
      if (str1[i - 1] === str2[j - 1]) {
        matrix[i][j] = matrix[i - 1][j - 1] + 1;

        if (matrix[i][j] > maxLength) {
          maxLength = matrix[i][j];
          endIndex = i - 1;
        }
      }
    }
  }

  // Extract the longest common substring using the endIndex
  const longestSubstring = str1.substr(endIndex - maxLength + 1, maxLength);
  return longestSubstring;
}

// Usage example
const str1 = 'abcdxyz';
const str2 = 'xyzabcd';
const longestSubstring = longestCommonSubstring(str1, str2);
console.log('Longest Common Substring:', longestSubstring);
